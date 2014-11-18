# pforeach
hoxo_m  



In usually, we describe some parallel processing code with `foreach`, for example:
  

```r
library(doParallel)
cl <- makeCluster(detectCores())
registerDoParallel(cl)
result <- foreach(i = 1:3, .combine=c) %dopar% {
  i**2
}
stopCluster(cl)
result
```

```
## [1] 1 4 9
```

But now, we can write the above code very simply using `pforeach`:


```r
library(pforeach)
result <- pforeach(i = 1:3)({
  i**2
})
result
```

```
## [1] 1 4 9
```


