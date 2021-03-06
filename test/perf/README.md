Updated: 1-22-2015

Latest performance tests of basic most.js operations.

```
> uname -a
Darwin bcavalier-2.home 14.0.0 Darwin Kernel Version 14.0.0: Fri Sep 19 00:26:44 PDT 2014; root:xnu-2782.1.97~2/RELEASE_X86_64 x86_64

> node --version
v0.11.14

> npm ls
most-perf@0.10.0 /Users/brian/Projects/cujojs/most/test/perf
├── baconjs@0.7.42
├─┬ benchmark@2.0.0-pre (git+https://github.com/bestiejs/benchmark.js#fc3ff3d865602b742ac2ef08e69d934815e08d36)
│ └── platform@1.3.0
├── highland@2.3.0
├── kefir@0.5.3
├── lodash@3.0.0-pre (git+https://github.com/lodash/lodash#de13d3866589b7ee2b7bbb96ff7fb7d4245fc875)
└── rx@2.3.24
```

```
filter -> map -> reduce 1000000 integers
-------------------------------------------------------
most        64.71 op/s ± 25.52%   (21 samples)
rx           0.58 op/s ±  1.87%    (6 samples)
kefir       10.44 op/s ±  1.93%   (29 samples)
bacon     FAILED: RangeError: Maximum call stack size exceeded
highland     4.79 op/s ±  3.04%   (16 samples)
lodash      20.45 op/s ±  2.77%   (37 samples)
Array        5.93 op/s ±  1.93%   (19 samples)
-------------------------------------------------------
```

```
flatMap 1000 x 1000 streams
-------------------------------------------------------
most        54.38 op/s ±  1.73%   (81 samples)
rx           0.36 op/s ±  3.52%    (5 samples)
kefir        9.43 op/s ±  2.32%   (26 samples)
bacon        0.86 op/s ±  2.80%    (7 samples)
highland     0.07 op/s ±  4.74%    (5 samples)
lodash      22.95 op/s ±  5.76%   (41 samples)
Array        0.37 op/s ±  3.02%    (5 samples)
-------------------------------------------------------
```

```
concatMap 1000 x 1000 streams
-------------------------------------------------------
most        53.38 op/s ±  0.67%   (81 samples)
rx           0.59 op/s ±  2.05%    (6 samples)
kefir       10.27 op/s ±  1.62%   (28 samples)
bacon        0.79 op/s ±  7.78%    (6 samples)
lodash      21.83 op/s ±  4.79%   (40 samples)
Array        0.37 op/s ±  1.91%    (5 samples)
-------------------------------------------------------
```

```
zip 2 x 100000 integers
-------------------------------------------------------
most        71.02 op/s ±  2.11%   (67 samples)
rx           1.11 op/s ±  2.93%    (7 samples)
kefir       29.68 op/s ±  1.56%   (38 samples)
bacon     FAILED: RangeError: Maximum call stack size exceeded
highland     0.23 op/s ±  6.99%    (5 samples)
lodash      23.61 op/s ±  5.50%   (42 samples)
-------------------------------------------------------
```

```
scan -> reduce 1000000 integers
-------------------------------------------------------
most        71.86 op/s ± 17.67%   (31 samples)
rx           0.62 op/s ±  1.96%    (6 samples)
kefir       16.74 op/s ±  0.77%   (42 samples)
bacon     FAILED: RangeError: Maximum call stack size exceeded
highland     4.23 op/s ±  5.33%   (15 samples)
lodash       6.49 op/s ± 11.49%   (20 samples)
Array        3.55 op/s ±  4.51%   (13 samples)
-------------------------------------------------------
```