---
title: "Broadband allowance being eaten by aliens."
date: 2010-12-29
forum: Networking &amp; Wireless
---

### Post by WarrenL on 2010-12-29
Dear all,

My buddy's Mint 10 computer appears to be slowly chewing  through his monthly broadband allowance. He's a complete non-tech  computer user, using the internet only for browsing and email. However  there appears to be a continous 600b/s upload going on. I don't really  know what I'm looking for, but I did find what follows in the excerpt  from tcpdump.txt.

Any ideas?

Best regards,
Warren


tcpdump.txt

```
11:53:07.637280 ARP, Request who-has 203.97.127.191 tell 203.97.117.0, length 46
11:53:07.640177 ARP, Request who-has 121.73.213.102 tell 121.72.229.0, length 46
11:53:07.779812 ARP, Request who-has 203.97.113.67 tell 203.97.117.0, length 46
11:53:07.886104 ARP, Request who-has 203.79.117.169 tell 203.97.117.0, length 46
11:53:07.906981 ARP, Request who-has 121.72.226.164 tell 121.72.229.0, length 46
11:53:07.946979 ARP, Request who-has 121.73.103.94 tell 121.72.229.0, length 46
11:53:08.002678 ARP, Request who-has 202.0.51.181 tell 203.97.117.0, length 46
11:53:08.136405 ARP, Request who-has 203.79.117.176 tell 203.97.117.0, length 46
11:53:08.229804 ARP, Request who-has 91.189.94.12 tell 121.73.101.49, length 28
11:53:08.238998 ARP, Reply 91.189.94.12 is-at 00:26:99:89:a8:e3, length 46
11:53:08.276027 ARP, Request who-has 121.73.114.120 tell 121.72.229.0, length 46
11:53:08.376183 ARP, Request who-has 202.78.155.126 tell 203.97.117.0, length 46
11:53:08.470504 ARP, Request who-has 203.79.116.35 tell 203.97.117.0, length 46
11:53:08.488096 ARP, Request who-has 121.72.224.92 tell 121.72.229.0, length 46
11:53:08.633878 ARP, Request who-has 121.73.113.225 tell 121.72.229.0, length 46
11:53:08.667297 ARP, Request who-has 202.78.153.100 tell 203.97.117.0, length 46
11:53:08.855446 ARP, Request who-has 203.79.117.180 tell 203.97.117.0, length 46
11:53:08.880463 ARP, Request who-has 121.72.226.243 tell 121.72.229.0, length 46
11:53:08.891125 ARP, Request who-has 203.97.125.176 tell 203.97.117.0, length 46
11:53:08.928654 ARP, Request who-has 203.97.113.196 tell 203.97.117.0, length 46
11:53:08.941129 ARP, Request who-has 202.0.51.39 tell 203.97.117.0, length 46
11:53:08.944496 ARP, Request who-has 203.97.113.199 tell 203.97.117.0, length 46
11:53:09.022702 ARP, Request who-has 121.72.227.180 tell 121.72.229.0, length 46
11:53:09.033102 ARP, Request who-has 121.73.99.97 tell 121.72.229.0, length 46
11:53:09.094379 ARP, Request who-has 202.78.158.103 tell 203.97.117.0, length 46
11:53:09.662535 ARP, Request who-has 203.97.114.210 tell 203.97.117.0, length 46
11:53:09.814973 ARP, Request who-has 203.97.118.78 tell 203.97.117.0, length 46
11:53:09.872260 ARP, Request who-has 203.97.113.209 tell 203.97.117.0, length 46
11:53:09.888690 ARP, Request who-has 203.97.113.212 tell 203.97.117.0, length 46
11:53:09.914840 ARP, Request who-has 203.97.113.217 tell 203.97.117.0, length 46
11:53:10.250914 ARP, Request who-has 121.73.109.224 tell 121.72.229.0, length 46
11:53:10.371714 ARP, Request who-has 203.97.123.139 tell 203.97.117.0, length 46
11:53:10.563610 ARP, Request who-has 121.73.213.102 tell 121.72.229.0, length 46
11:53:10.625479 ARP, Request who-has 203.97.127.191 tell 203.97.117.0, length 46
11:53:10.890747 ARP, Request who-has 121.72.226.243 tell 121.72.229.0, length 46
11:53:10.924354 ARP, Request who-has 203.97.113.243 tell 203.97.117.0, length 46
11:53:11.300788 ARP, Request who-has 121.73.113.225 tell 121.72.229.0, length 46
11:53:11.319589 ARP, Request who-has 203.97.125.176 tell 203.97.117.0, length 46
11:53:11.541181 ARP, Request who-has 121.73.217.239 tell 121.72.229.0, length 46
11:53:11.711427 ARP, Request who-has 121.73.216.149 tell 121.72.229.0, length 46
11:53:11.807155 ARP, Request who-has 121.73.221.186 tell 121.72.229.0, length 46
11:53:12.033235 ARP, Request who-has 203.97.123.10 tell 203.97.117.0, length 46
11:53:12.159338 ARP, Request who-has 121.73.102.136 tell 121.72.229.0, length 46
11:53:12.779163 ARP, Request who-has 203.97.127.205 tell 203.97.117.0, length 46
11:53:13.044863 ARP, Request who-has 121.72.226.243 tell 121.72.229.0, length 46
11:53:13.137390 ARP, Request who-has 203.97.123.45 tell 203.97.117.0, length 46
11:53:13.162461 ARP, Request who-has 203.97.112.3 tell 203.97.117.0, length 46
11:53:13.206796 ARP, Request who-has 203.97.112.21 tell 203.97.117.0, length 46
11:53:13.452744 ARP, Request who-has 203.97.112.27 tell 203.97.117.0, length 46
11:53:13.468754 ARP, Request who-has 121.73.219.57 tell 121.72.229.0, length 46
11:53:13.723654 ARP, Request who-has 121.73.216.149 tell 121.72.229.0, length 46
11:53:13.790275 ARP, Request who-has 203.97.120.144 tell 203.97.117.0, length 46
11:53:13.964404 ARP, Request who-has 121.73.126.180 tell 121.72.229.0, length 46
11:53:14.011968 ARP, Request who-has 203.97.123.59 tell 203.97.117.0, length 46
11:53:14.168606 ARP, Request who-has 203.97.112.28 tell 203.97.117.0, length 46
11:53:14.174814 ARP, Request who-has 203.97.112.30 tell 203.97.117.0, length 46
11:53:14.202521 ARP, Request who-has 203.97.112.41 tell 203.97.117.0, length 46
11:53:14.278541 ARP, Request who-has 121.73.114.120 tell 121.72.229.0, length 46
11:53:14.393395 ARP, Request who-has 121.73.217.239 tell 121.72.229.0, length 46
11:53:14.685055 ARP, Request who-has 121.73.118.21 tell 121.72.229.0, length 46
11:53:14.703097 ARP, Request who-has 121.73.221.186 tell 121.72.229.0, length 46
11:53:14.707764 ARP, Request who-has 121.73.123.157 tell 121.72.229.0, length 46
11:53:14.763797 ARP, Request who-has 203.97.127.254 tell 203.97.117.0, length 46
11:53:14.909978 ARP, Request who-has 203.97.123.139 tell 203.97.117.0, length 46
11:53:15.033838 ARP, Request who-has 121.73.99.97 tell 121.72.229.0, length 46
11:53:15.037176 ARP, Request who-has 203.97.123.85 tell 203.97.117.0, length 46
11:53:15.050905 ARP, Request who-has 203.97.115.173 tell 203.97.117.0, length 46
11:53:15.214921 ARP, Request who-has 203.97.112.67 tell 203.97.117.0, length 46
11:53:15.327722 ARP, Request who-has 203.97.125.176 tell 203.97.117.0, length 46
11:53:15.367361 ARP, Request who-has 121.73.113.225 tell 121.72.229.0, length 46
11:53:15.419530 ARP, Request who-has 202.78.152.167 tell 203.97.117.0, length 46
11:53:15.535608 ARP, Request who-has 121.72.226.243 tell 121.72.229.0, length 46
11:53:15.565394 ARP, Request who-has 203.97.119.46 tell 203.97.117.0, length 46
11:53:15.756033 ARP, Request who-has 202.0.51.64 tell 203.97.117.0, length 46
11:53:15.963998 ARP, Request who-has 203.79.116.30 tell 203.97.117.0, length 46
11:53:16.202520 ARP, Request who-has 203.97.112.84 tell 203.97.117.0, length 46
11:53:16.210676 ARP, Request who-has 203.97.112.87 tell 203.97.117.0, length 46
11:53:16.231647 ARP, Request who-has 203.97.112.96 tell 203.97.117.0, length 46
11:53:16.290935 ARP, Request who-has 121.73.115.9 tell 121.72.229.0, length 46
11:53:16.343015 ARP, Request who-has 203.167.133.36 tell 203.97.117.0, length 46
11:53:16.349052 ARP, Request who-has 203.167.133.42 tell 203.97.117.0, length 46
11:53:16.486409 ARP, Request who-has 203.97.119.55 tell 203.97.117.0, length 46
11:53:16.507071 ARP, Request who-has 203.97.119.58 tell 203.97.117.0, length 46
11:53:16.617360 ARP, Request who-has 203.97.120.144 tell 203.97.117.0, length 46
11:53:16.618242 ARP, Request who-has 203.97.127.191 tell 203.97.117.0, length 46
11:53:16.968566 ARP, Request who-has 121.73.107.13 tell 121.72.229.0, length 46
11:53:17.042228 ARP, Request who-has 203.97.123.139 tell 203.97.117.0, length 46
11:53:17.198090 ARP, Request who-has 202.0.56.111 tell 203.97.117.0, length 46
11:53:17.382589 ARP, Request who-has 121.73.113.225 tell 121.72.229.0, length 46
11:53:17.392135 ARP, Request who-has 203.97.121.107 tell 203.97.117.0, length 46
11:53:17.466341 ARP, Request who-has 202.78.152.167 tell 203.97.117.0, length 46
11:53:17.544283 ARP, Request who-has 121.72.225.173 tell 121.72.229.0, length 46
11:53:17.567597 ARP, Request who-has 203.97.119.95 tell 203.97.117.0, length 46
11:53:17.629816 ARP, Request who-has 121.72.226.243 tell 121.72.229.0, length 46
11:53:17.670284 ARP, Request who-has 202.78.159.36 tell 203.97.117.0, length 46
11:53:17.685109 ARP, Request who-has 121.73.118.21 tell 121.72.229.0, length 46
11:53:17.727678 ARP, Request who-has 121.73.216.149 tell 121.72.229.0, length 46
11:53:18.061401 ARP, Request who-has 203.97.115.173 tell 203.97.117.0, length 46
11:53:18.203498 ARP, Request who-has 121.73.121.64 tell 121.72.229.0, length 46
11:53:18.235493 ARP, Request who-has 203.97.112.140 tell 203.97.117.0, length 46
11:53:18.262322 ARP, Request who-has 203.97.112.151 tell 203.97.117.0, length 46
11:53:18.262682 ARP, Request who-has 121.73.119.239 tell 121.72.229.0, length 46
11:53:18.360726 ARP, Request who-has 203.167.133.85 tell 203.97.117.0, length 46
11:53:18.561286 ARP, Request who-has 203.97.119.118 tell 203.97.117.0, length 46
11:53:18.659457 ARP, Request who-has 203.79.117.51 tell 203.97.117.0, length 46
11:53:18.865879 ARP, Request who-has 203.97.117.10 tell 203.97.117.0, length 46
11:53:18.898650 ARP, Request who-has 202.78.153.100 tell 203.97.117.0, length 46
11:53:18.933225 ARP, Request who-has 203.79.116.30 tell 203.97.117.0, length 46
11:53:18.976990 ARP, Request who-has 202.0.51.52 tell 203.97.117.0, length 46
11:53:19.001269 ARP, Request who-has 10.35.135.105 tell 10.35.128.1, length 46
11:53:19.001717 ARP, Request who-has 10.35.139.190 tell 10.35.128.1, length 46
11:53:19.149845 ARP, Request who-has 203.167.133.103 tell 203.97.117.0, length 46
11:53:19.233227 ARP, Request who-has 203.97.112.162 tell 203.97.117.0, length 46
11:53:19.237589 ARP, Request who-has 121.73.115.9 tell 121.72.229.0, length 46
11:53:19.245297 ARP, Request who-has 203.97.112.167 tell 203.97.117.0, length 46
11:53:19.372661 ARP, Request who-has 121.72.253.48 tell 121.72.229.0, length 46
11:53:19.588617 ARP, Request who-has 203.97.123.139 tell 203.97.117.0, length 46
11:53:19.589940 ARP, Request who-has 203.97.119.148 tell 203.97.117.0, length 46
11:53:19.775339 ARP, Request who-has 121.73.223.195 tell 121.72.229.0, length 46
11:53:19.883454 ARP, Request who-has 202.78.158.103 tell 203.97.117.0, length 46
11:53:19.947319 ARP, Request who-has 203.97.112.3 tell 203.97.117.0, length 46
11:53:19.999901 ARP, Request who-has 203.97.112.21 tell 203.97.117.0, length 46
11:53:20.049919 ARP, Request who-has 203.97.123.214 tell 203.97.117.0, length 46
11:53:20.066278 ARP, Request who-has 202.0.56.111 tell 203.97.117.0, length 46
11:53:20.180829 ARP, Request who-has 203.97.112.27 tell 203.97.117.0, length 46
11:53:20.281350 ARP, Request who-has 203.97.112.202 tell 203.97.117.0, length 46
11:53:20.375882 ARP, Request who-has 203.167.133.142 tell 203.97.117.0, length 46
11:53:20.386463 ARP, Request who-has 203.97.121.107 tell 203.97.117.0, length 46
11:53:20.391880 ARP, Request who-has 203.167.133.151 tell 203.97.117.0, length 46
11:53:20.493450 ARP, Request who-has 121.72.234.60 tell 121.72.229.0, length 46
11:53:20.551803 ARP, Request who-has 203.97.119.165 tell 203.97.117.0, length 46
11:53:20.643913 ARP, Request who-has 202.78.159.36 tell 203.97.117.0, length 46
11:53:20.907701 ARP, Request who-has 121.72.224.108 tell 121.72.229.0, length 46
11:53:20.955126 ARP, Request who-has 203.97.112.28 tell 203.97.117.0, length 46
11:53:20.967673 ARP, Request who-has 203.97.112.30 tell 203.97.117.0, length 46
11:53:20.993528 ARP, Request who-has 203.97.112.41 tell 203.97.117.0, length 46
11:53:21.008835 ARP, Request who-has 202.78.153.100 tell 203.97.117.0, length 46
11:53:21.261975 ARP, Request who-has 203.97.112.218 tell 203.97.117.0, length 46
11:53:21.368706 ARP, Request who-has 121.73.113.225 tell 121.72.229.0, length 46
11:53:21.370584 ARP, Request who-has 121.73.119.239 tell 121.72.229.0, length 46
11:53:21.377700 ARP, Request who-has 203.167.133.158 tell 203.97.117.0, length 46
11:53:21.410068 ARP, Request who-has 203.167.133.173 tell 203.97.117.0, length 46
11:53:21.431726 ARP, Request who-has 121.73.105.80 tell 121.72.229.0, length 46
11:53:21.496861 ARP, Request who-has 202.78.152.167 tell 203.97.117.0, length 46
11:53:21.576830 ARP, Request who-has 203.79.117.51 tell 203.97.117.0, length 46
11:53:21.677186 ARP, Request who-has 121.72.226.243 tell 121.72.229.0, length 46
11:53:21.789644 ARP, Request who-has 203.97.117.10 tell 203.97.117.0, length 46
11:53:21.834001 ARP, Request who-has 202.0.51.52 tell 203.97.117.0, length 46
11:53:21.947576 ARP, Request who-has 121.73.220.26 tell 121.72.229.0, length 46
11:53:21.969637 ARP, Request who-has 121.73.126.180 tell 121.72.229.0, length 46
11:53:21.998750 ARP, Request who-has 203.97.112.67 tell 203.97.117.0, length 46
11:53:22.077860 ARP, Request who-has 202.0.56.111 tell 203.97.117.0, length 46
11:53:22.375336 ARP, Request who-has 121.72.253.48 tell 121.72.229.0, length 46
11:53:22.376318 ARP, Request who-has 203.167.133.184 tell 203.97.117.0, length 46
11:53:22.402772 ARP, Request who-has 10.35.139.190 tell 10.35.128.1, length 46
11:53:22.403164 ARP, Request who-has 10.35.135.105 tell 10.35.128.1, length 46
11:53:22.483071 ARP, Request who-has 121.73.223.195 tell 121.72.229.0, length 46
11:53:22.584682 ARP, Request who-has 121.73.121.64 tell 121.72.229.0, length 46
11:53:22.621725 ARP, Request who-has 203.97.119.228 tell 203.97.117.0, length 46
11:53:22.803939 ARP, Request who-has 202.78.158.103 tell 203.97.117.0, length 46
11:53:22.913043 ARP, Request who-has 121.73.117.220 tell 121.72.229.0, length 46
11:53:22.992146 ARP, Request who-has 203.97.112.84 tell 203.97.117.0, length 46
11:53:22.993886 ARP, Request who-has 203.97.112.87 tell 203.97.117.0, length 46
11:53:23.029272 ARP, Request who-has 203.97.112.96 tell 203.97.117.0, length 46
11:53:23.064506 ARP, Request who-has 202.78.158.120 tell 203.97.117.0, length 46
11:53:23.112141 ARP, Request who-has 202.78.153.100 tell 203.97.117.0, length 46
11:53:23.410795 ARP, Request who-has 121.72.234.60 tell 121.72.229.0, length 46
11:53:23.411788 ARP, Request who-has 121.73.113.225 tell 121.72.229.0, length 46
11:53:23.415994 ARP, Request who-has 203.97.119.240 tell 203.97.117.0, length 46
11:53:23.570198 ARP, Request who-has 203.97.119.242 tell 203.97.117.0, length 46
11:53:23.676108 ARP, Request who-has 121.73.109.95 tell 121.72.229.0, length 46
11:53:23.690993 ARP, Request who-has 121.73.117.146 tell 121.72.229.0, length 46
11:53:23.782425 ARP, Request who-has 121.72.226.243 tell 121.72.229.0, length 46
11:53:23.789364 ARP, Request who-has 203.97.120.144 tell 203.97.117.0, length 46
11:53:23.794030 ARP, Request who-has 121.72.224.108 tell 121.72.229.0, length 46
11:53:23.824018 ARP, Request who-has 121.72.225.173 tell 121.72.229.0, length 46
11:53:23.827758 ARP, Request who-has 121.72.230.112 tell 121.72.229.0, length 46
11:53:24.151954 ARP, Request who-has 121.73.216.70 tell 121.72.229.0, length 46
11:53:24.227092 ARP, Request who-has 121.73.126.156 tell 121.72.229.0, length 46
11:53:24.276706 ARP, Request who-has 121.73.214.25 tell 121.72.229.0, length 46
11:53:24.391388 ARP, Request who-has 203.167.133.233 tell 203.97.117.0, length 46
11:53:24.395954 ARP, Request who-has 121.73.105.80 tell 121.72.229.0, length 46
11:53:24.402957 ARP, Request who-has 121.72.242.16 tell 121.72.229.0, length 46
11:53:24.508261 ARP, Request who-has 121.73.105.191 tell 121.72.229.0, length 46
11:53:24.566634 ARP, Request who-has 121.73.119.239 tell 121.72.229.0, length 46
11:53:24.595097 ARP, Request who-has 203.97.126.7 tell 203.97.117.0, length 46
11:53:24.742049 ARP, Request who-has 121.73.219.57 tell 121.72.229.0, length 46
11:53:24.862683 ARP, Request who-has 121.73.220.26 tell 121.72.229.0, length 46
11:53:24.942832 ARP, Request who-has 121.73.117.220 tell 121.72.229.0, length 46
11:53:24.982099 ARP, Request who-has 121.73.219.115 tell 121.72.229.0, length 46
11:53:25.025209 ARP, Request who-has 203.97.112.140 tell 203.97.117.0, length 46
11:53:25.046142 ARP, Request who-has 203.97.112.151 tell 203.97.117.0, length 46
11:53:25.184080 ARP, Request who-has 203.97.118.170 tell 203.97.117.0, length 46
11:53:25.244643 ARP, Request who-has 202.78.153.100 tell 203.97.117.0, length 46
11:53:25.502080 ARP, Request who-has 121.73.101.222 tell 121.72.229.0, length 46
11:53:25.619196 ARP, Request who-has 121.73.99.97 tell 121.72.229.0, length 46
11:53:25.662580 ARP, Request who-has 121.73.114.11 tell 121.72.229.0, length 46
11:53:25.906430 ARP, Request who-has 202.78.158.103 tell 203.97.117.0, length 46
11:53:26.019237 ARP, Request who-has 203.97.112.162 tell 203.97.117.0, length 46
11:53:26.030196 ARP, Request who-has 121.73.126.180 tell 121.72.229.0, length 46
11:53:26.030575 ARP, Request who-has 203.97.112.167 tell 203.97.117.0, length 46
11:53:26.090597 ARP, Request who-has 202.78.158.120 tell 203.97.117.0, length 46
11:53:26.263805 ARP, Request who-has 121.72.226.243 tell 121.72.229.0, length 46
11:53:26.360654 ARP, Request who-has 121.72.230.112 tell 121.72.229.0, length 46
11:53:26.499381 ARP, Request who-has 121.73.109.231 tell 121.72.229.0, length 46
11:53:26.590948 ARP, Request who-has 121.73.59.153 tell 121.72.229.0, length 46
11:53:26.617497 ARP, Request who-has 203.97.120.144 tell 203.97.117.0, length 46
11:53:26.956320 ARP, Request who-has 203.97.127.191 tell 203.97.117.0, length 46
11:53:27.043922 ARP, Request who-has 121.73.216.70 tell 121.72.229.0, length 46
11:53:27.070487 ARP, Request who-has 203.97.112.202 tell 203.97.117.0, length 46
11:53:27.170009 ARP, Request who-has 121.73.126.156 tell 121.72.229.0, length 46
11:53:27.183070 ARP, Request who-has 121.73.103.94 tell 121.72.229.0, length 46
11:53:27.258303 ARP, Request who-has 121.73.214.25 tell 121.72.229.0, length 46
11:53:27.260677 ARP, Request who-has 203.97.127.205 tell 203.97.117.0, length 46
11:53:27.285447 ARP, Request who-has 203.79.68.29 tell 203.97.117.0, length 46
11:53:27.334567 ARP, Request who-has 121.72.242.16 tell 121.72.229.0, length 46
11:53:27.360385 ARP, Request who-has 121.73.113.225 tell 121.72.229.0, length 46
11:53:27.370507 ARP, Request who-has 202.78.153.100 tell 203.97.117.0, length 46
11:53:27.451218 ARP, Request who-has 121.73.105.191 tell 121.72.229.0, length 46
11:53:27.467312 ARP, Request who-has 203.97.113.6 tell 203.97.117.0, length 46
11:53:27.564952 ARP, Request who-has 203.97.126.7 tell 203.97.117.0, length 46
11:53:27.622384 ARP, Request who-has 121.73.117.220 tell 121.72.229.0, length 46
11:53:27.929262 ARP, Request who-has 121.73.219.115 tell 121.72.229.0, length 46
11:53:28.050095 ARP, Request who-has 203.97.112.218 tell 203.97.117.0, length 46
11:53:28.093821 ARP, Request who-has 202.0.56.111 tell 203.97.117.0, length 46
11:53:28.240185 ARP, Request who-has 121.73.214.157 tell 121.72.229.0, length 46
11:53:28.375348 ARP, Request who-has 121.72.253.48 tell 121.72.229.0, length 46
11:53:28.437029 ARP, Request who-has 203.97.122.117 tell 203.97.117.0, length 46
11:53:28.630617 ARP, Request who-has 203.97.112.41 tell 203.97.117.0, length 46
11:53:28.631582 ARP, Request who-has 121.73.114.11 tell 121.72.229.0, length 46
11:53:28.740476 ARP, Request who-has 121.72.230.112 tell 121.72.229.0, length 46
11:53:28.905865 ARP, Request who-has 202.78.158.103 tell 203.97.117.0, length 46
11:53:29.072620 ARP, Request who-has 121.72.226.243 tell 121.72.229.0, length 46
11:53:29.147996 ARP, Request who-has 121.73.121.14 tell 121.72.229.0, length 46
11:53:29.241972 ARP, Request who-has 203.97.127.254 tell 203.97.117.0, length 46
11:53:29.309028 ARP, Request who-has 121.73.106.107 tell 121.72.229.0, length 46
11:53:29.579065 ARP, Request who-has 121.73.59.153 tell 121.72.229.0, length 46
11:53:29.613727 ARP, Request who-has 121.72.233.211 tell 121.72.229.0, length 46
11:53:30.172866 ARP, Request who-has 121.72.224.106 tell 121.72.229.0, length 46
11:53:30.192046 ARP, Request who-has 121.73.103.94 tell 121.72.229.0, length 46
11:53:30.287053 ARP, Request who-has 121.73.119.239 tell 121.72.229.0, length 46
11:53:30.634809 ARP, Request who-has 121.73.216.149 tell 121.72.229.0, length 46
11:53:30.754884 ARP, Request who-has 121.73.214.157 tell 121.72.229.0, length 46
11:53:30.895269 ARP, Request who-has 121.73.220.26 tell 121.72.229.0, length 46
11:53:31.005513 ARP, Request who-has 121.73.96.25 tell 121.72.229.0, length 46
11:53:31.121258 ARP, Request who-has 203.79.117.42 tell 203.97.117.0, length 46
11:53:31.354139 ARP, Request who-has 203.97.127.191 tell 203.97.117.0, length 46
11:53:31.489266 ARP, Request who-has 203.79.117.51 tell 203.97.117.0, length 46
11:53:31.525202 ARP, Request who-has 202.0.56.219 tell 203.97.117.0, length 46
11:53:31.555777 ARP, Request who-has 121.73.113.179 tell 121.72.229.0, length 46
11:53:31.661182 ARP, Request who-has 203.97.112.41 tell 203.97.117.0, length 46
11:53:31.676026 ARP, Request who-has 121.72.226.243 tell 121.72.229.0, length 46
11:53:31.930584 ARP, Request who-has 203.97.125.128 tell 203.97.117.0, length 46
11:53:32.214061 ARP, Request who-has 203.97.119.242 tell 203.97.117.0, length 46
11:53:32.255921 ARP, Request who-has 121.73.121.14 tell 121.72.229.0, length 46
11:53:32.257709 ARP, Request who-has 121.73.106.107 tell 121.72.229.0, length 46
11:53:32.319065 ARP, Request who-has 121.72.225.173 tell 121.72.229.0, length 46
11:53:32.688193 ARP, Request who-has 121.73.216.149 tell 121.72.229.0, length 46
11:53:32.752364 ARP, Request who-has 121.73.222.27 tell 121.72.229.0, length 46
11:53:32.932112 ARP, Request who-has 121.72.234.60 tell 121.72.229.0, length 46
11:53:33.137184 ARP, Request who-has 121.72.224.106 tell 121.72.229.0, length 46
11:53:33.220655 ARP, Request who-has 121.72.227.180 tell 121.72.229.0, length 46
11:53:33.255096 ARP, Request who-has 121.73.216.100 tell 121.72.229.0, length 46
11:53:33.255593 ARP, Request who-has 121.73.221.68 tell 121.72.229.0, length 46
11:53:33.324613 ARP, Request who-has 121.73.96.25 tell 121.72.229.0, length 46
11:53:33.365904 ARP, Request who-has 121.73.113.225 tell 121.72.229.0, length 46
11:53:33.444750 ARP, Request who-has 121.73.101.82 tell 121.72.229.0, length 46
11:53:33.709512 ARP, Request who-has 121.73.214.157 tell 121.72.229.0, length 46
11:53:33.789920 ARP, Request who-has 203.97.120.144 tell 203.97.117.0, length 46
11:53:34.246665 ARP, Request who-has 203.97.119.242 tell 203.97.117.0, length 46
11:53:34.303309 ARP, Request who-has 121.73.219.57 tell 121.72.229.0, length 46
11:53:34.509753 ARP, Request who-has 121.73.113.179 tell 121.72.229.0, length 46
11:53:34.830871 ARP, Request who-has 203.97.125.128 tell 203.97.117.0, length 46
11:53:35.115627 ARP, Request who-has 121.73.216.149 tell 121.72.229.0, length 46
11:53:35.283448 ARP, Request who-has 121.73.123.157 tell 121.72.229.0, length 46
11:53:35.433689 ARP, Request who-has 121.73.111.71 tell 121.72.229.0, length 46
11:53:35.670528 ARP, Request who-has 202.78.159.39 tell 203.97.117.0, length 46
11:53:35.826659 ARP, Request who-has 121.72.225.173 tell 121.72.229.0, length 46
11:53:35.986881 ARP, Request who-has 121.73.117.220 tell 121.72.229.0, length 46
11:53:35.992991 ARP, Request who-has 121.72.226.243 tell 121.72.229.0, length 46
11:53:35.995548 ARP, Request who-has 202.0.58.161 tell 203.97.117.0, length 46
11:53:36.106884 ARP, Request who-has 202.0.56.111 tell 203.97.117.0, length 46
11:53:36.170272 ARP, Request who-has 121.73.221.68 tell 121.72.229.0, length 46
11:53:36.208995 ARP, Request who-has 203.79.117.169 tell 203.97.117.0, length 46
11:53:36.274319 IP 121.73.101.49.45524 > 203.96.152.4.53: 705+ A? weather.noaa.gov. (34)
11:53:36.458089 ARP, Request who-has 121.73.223.73 tell 121.72.229.0, length 46
11:53:36.489075 ARP, Request who-has 121.73.101.82 tell 121.72.229.0, length 46
11:53:36.539478 ARP, Request who-has 203.79.117.176 tell 203.97.117.0, length 46
11:53:36.618145 ARP, Request who-has 203.97.120.144 tell 203.97.117.0, length 46
11:53:37.054778 ARP, Request who-has 121.73.219.57 tell 121.72.229.0, length 46
11:53:37.115098 ARP, Request who-has 203.79.117.180 tell 203.97.117.0, length 46
11:53:37.370087 ARP, Request who-has 203.167.134.93 tell 203.97.117.0, length 46
11:53:37.389690 ARP, Request who-has 121.73.223.195 tell 121.72.229.0, length 46
11:53:37.583102 ARP, Request who-has 202.78.153.100 tell 203.97.117.0, length 46
11:53:37.708248 ARP, Request who-has 121.73.223.69 tell 121.72.229.0, length 46
11:53:37.712072 ARP, Request who-has 202.78.159.39 tell 203.97.117.0, length 46
11:53:38.001837 ARP, Request who-has 121.73.117.220 tell 121.72.229.0, length 46
11:53:38.278713 ARP, Request who-has 203.97.119.242 tell 203.97.117.0, length 46
11:53:38.365132 ARP, Request who-has 121.73.111.71 tell 121.72.229.0, length 46
11:53:41.277887 IP 121.73.101.49.45524 > 203.96.152.4.53: 705+ A? weather.noaa.gov. (34)
11:53:41.285826 ARP, Request who-has 203.96.152.4 tell 121.73.101.49, length 28
11:53:42.285825 ARP, Request who-has 203.96.152.4 tell 121.73.101.49, length 28
11:53:43.285807 ARP, Request who-has 203.96.152.4 tell 121.73.101.49, length 28
11:53:46.285806 ARP, Request who-has 203.96.152.4 tell 121.73.101.49, length 28
11:53:47.285818 ARP, Request who-has 203.96.152.4 tell 121.73.101.49, length 28
11:53:48.285813 ARP, Request who-has 203.96.152.4 tell 121.73.101.49, length 28
11:53:51.285845 ARP, Request who-has 203.96.152.4 tell 121.73.101.49, length 28
11:53:52.285809 ARP, Request who-has 203.96.152.4 tell 121.73.101.49, length 28
11:53:53.285811 ARP, Request who-has 203.96.152.4 tell 121.73.101.49, length 28
11:54:55.185794  IP 121.73.101.49.59025 > 203.97.30.144.80: Flags [F.], seq  3101650020, ack 2734447218, win 454, options [nop,nop,TS val 2729270 ecr  1232726303], length 0
11:54:55.185887 IP 121.73.101.49.42981 >  203.97.30.145.80: Flags [F.], seq 3098986732, ack 2726517781, win 118,  options [nop,nop,TS val 2729271 ecr 1232725395], length 0
11:54:55.409855  IP 121.73.101.49.59025 > 203.97.30.144.80: Flags [F.], seq 0, ack 1,  win 454, options [nop,nop,TS val 2729327 ecr 1232726303], length 0
11:54:55.409892  IP 121.73.101.49.42981 > 203.97.30.145.80: Flags [F.], seq 0, ack 1,  win 118, options [nop,nop,TS val 2729327 ecr 1232725395], length 0
11:54:55.857848  IP 121.73.101.49.59025 > 203.97.30.144.80: Flags [F.], seq 0, ack 1,  win 454, options [nop,nop,TS val 2729439 ecr 1232726303], length 0
11:54:55.857883  IP 121.73.101.49.42981 > 203.97.30.145.80: Flags [F.], seq 0, ack 1,  win 118, options [nop,nop,TS val 2729439 ecr 1232725395], length 0
11:54:56.753864  IP 121.73.101.49.59025 > 203.97.30.144.80: Flags [F.], seq 0, ack 1,  win 454, options [nop,nop,TS val 2729663 ecr 1232726303], length 0
11:54:56.753904  IP 121.73.101.49.42981 > 203.97.30.145.80: Flags [F.], seq 0, ack 1,  win 118, options [nop,nop,TS val 2729663 ecr 1232725395], length 0
11:54:58.549878  IP 121.73.101.49.59025 > 203.97.30.144.80: Flags [F.], seq 0, ack 1,  win 454, options [nop,nop,TS val 2730112 ecr 1232726303], length 0
11:54:58.549949  IP 121.73.101.49.42981 > 203.97.30.145.80: Flags [F.], seq 0, ack 1,  win 118, options [nop,nop,TS val 2730112 ecr 1232725395], length 0
11:55:00.197833 ARP, Request who-has 203.97.30.144 tell 121.73.101.49, length 28
11:55:00.197860 ARP, Request who-has 203.97.30.145 tell 121.73.101.49, length 28
11:55:01.197820 ARP, Request who-has 203.97.30.144 tell 121.73.101.49, length 28
11:55:01.197836 ARP, Request who-has 203.97.30.145 tell 121.73.101.49, length 28
11:55:02.141874  IP 121.73.101.49.59025 > 203.97.30.144.80: Flags [F.], seq 0, ack 1,  win 454, options [nop,nop,TS val 2731010 ecr 1232726303], length 0
11:55:02.141925  IP 121.73.101.49.42981 > 203.97.30.145.80: Flags [F.], seq 0, ack 1,  win 118, options [nop,nop,TS val 2731010 ecr 1232725395], length 0
11:55:02.197803 ARP, Request who-has 203.97.30.144 tell 121.73.101.49, length 28
11:55:02.197818 ARP, Request who-has 203.97.30.145 tell 121.73.101.49, length 28
11:55:09.337806 ARP, Request who-has 203.97.30.144 tell 121.73.101.49, length 28
11:55:09.337824 ARP, Request who-has 203.97.30.145 tell 121.73.101.49, length 28
11:55:10.337813 ARP, Request who-has 203.97.30.144 tell 121.73.101.49, length 28
11:55:10.337832 ARP, Request who-has 203.97.30.145 tell 121.73.101.49, length 28
11:55:11.337852 ARP, Request who-has 203.97.30.144 tell 121.73.101.49, length 28
11:55:11.337889 ARP, Request who-has 203.97.30.145 tell 121.73.101.49, length 28
11:55:16.521818 ARP, Request who-has 203.97.30.144 tell 121.73.101.49, length 28
11:55:16.521839 ARP, Request who-has 203.97.30.145 tell 121.73.101.49, length 28
11:55:17.521804 ARP, Request who-has 203.97.30.144 tell 121.73.101.49, length 28
11:55:17.521826 ARP, Request who-has 203.97.30.145 tell 121.73.101.49, length 28
11:55:18.521807 ARP, Request who-has 203.97.30.144 tell 121.73.101.49, length 28
11:55:18.521827 ARP, Request who-has 203.97.30.145 tell 121.73.101.49, length 28
11:55:23.705806 ARP, Request who-has 203.97.30.144 tell 121.73.101.49, length 28
11:55:23.705822 ARP, Request who-has 203.97.30.145 tell 121.73.101.49, length 28
11:55:24.705832 ARP, Request who-has 203.97.30.144 tell 121.73.101.49, length 28
11:55:24.705858 ARP, Request who-has 203.97.30.145 tell 121.73.101.49, length 28
11:55:25.705834 ARP, Request who-has 203.97.30.144 tell 121.73.101.49, length 28
11:55:25.705859 ARP, Request who-has 203.97.30.145 tell 121.73.101.49, length 28
11:55:30.889806 ARP, Request who-has 203.97.30.144 tell 121.73.101.49, length 28
11:55:30.889823 ARP, Request who-has 203.97.30.145 tell 121.73.101.49, length 28
11:55:31.889818 ARP, Request who-has 203.97.30.144 tell 121.73.101.49, length 28
11:55:31.889839 ARP, Request who-has 203.97.30.145 tell 121.73.101.49, length 28
11:55:32.889810 ARP, Request who-has 203.97.30.144 tell 121.73.101.49, length 28
11:55:32.889829 ARP, Request who-has 203.97.30.145 tell 121.73.101.49, length 28
11:55:38.073804 ARP, Request who-has 203.97.30.144 tell 121.73.101.49, length 28
11:55:38.073822 ARP, Request who-has 203.97.30.145 tell 121.73.101.49, length 28
11:55:39.073808 ARP, Request who-has 203.97.30.144 tell 121.73.101.49, length 28
11:55:39.073829 ARP, Request who-has 203.97.30.145 tell 121.73.101.49, length 28
11:55:40.073810 ARP, Request who-has 203.97.30.144 tell 121.73.101.49, length 28
11:55:40.073829 ARP, Request who-has 203.97.30.145 tell 121.73.101.49, length 28
11:55:45.257806 ARP, Request who-has 203.97.30.144 tell 121.73.101.49, length 28
11:55:45.257823 ARP, Request who-has 203.97.30.145 tell 121.73.101.49, length 28
11:55:46.257810 ARP, Request who-has 203.97.30.144 tell 121.73.101.49, length 28
11:55:46.257829 ARP, Request who-has 203.97.30.145 tell 121.73.101.49, length 28
11:55:47.257814 ARP, Request who-has 203.97.30.144 tell 121.73.101.49, length 28
11:55:47.257833 ARP, Request who-has 203.97.30.145 tell 121.73.101.49, length 28
11:55:52.441807 ARP, Request who-has 203.97.30.144 tell 121.73.101.49, length 28
11:55:52.441824 ARP, Request who-has 203.97.30.145 tell 121.73.101.49, length 28
11:55:53.441809 ARP, Request who-has 203.97.30.144 tell 121.73.101.49, length 28
11:55:53.441828 ARP, Request who-has 203.97.30.145 tell 121.73.101.49, length 28
11:55:54.441811 ARP, Request who-has 203.97.30.144 tell 121.73.101.49, length 28
11:55:54.441830 ARP, Request who-has 203.97.30.145 tell 121.73.101.49, length 28
11:55:59.625848 ARP, Request who-has 203.97.30.144 tell 121.73.101.49, length 28
11:55:59.625883 ARP, Request who-has 203.97.30.145 tell 121.73.101.49, length 28
11:56:00.625810 ARP, Request who-has 203.97.30.144 tell 121.73.101.49, length 28
11:56:00.625829 ARP, Request who-has 203.97.30.145 tell 121.73.101.49, length 28
11:56:01.625812 ARP, Request who-has 203.97.30.144 tell 121.73.101.49, length 28
11:56:01.625830 ARP, Request who-has 203.97.30.145 tell 121.73.101.49, length 28
11:56:06.809805 ARP, Request who-has 203.97.30.144 tell 121.73.101.49, length 28
11:56:06.809823 ARP, Request who-has 203.97.30.145 tell 121.73.101.49, length 28
11:56:07.809810 ARP, Request who-has 203.97.30.144 tell 121.73.101.49, length 28
11:56:07.809829 ARP, Request who-has 203.97.30.145 tell 121.73.101.49, length 28
11:56:08.809813 ARP, Request who-has 203.97.30.144 tell 121.73.101.49, length 28
11:56:08.809831 ARP, Request who-has 203.97.30.145 tell 121.73.101.49, length 28
11:56:13.993806 ARP, Request who-has 203.97.30.144 tell 121.73.101.49, length 28
11:56:13.993828 ARP, Request who-has 203.97.30.145 tell 121.73.101.49, length 28
11:56:14.993810 ARP, Request who-has 203.97.30.144 tell 121.73.101.49, length 28
11:56:14.993830 ARP, Request who-has 203.97.30.145 tell 121.73.101.49, length 28
11:56:15.993815 ARP, Request who-has 203.97.30.144 tell 121.73.101.49, length 28
11:56:15.993838 ARP, Request who-has 203.97.30.145 tell 121.73.101.49, length 28
11:56:21.177805 ARP, Request who-has 203.97.30.144 tell 121.73.101.49, length 28
11:56:21.177825 ARP, Request who-has 203.97.30.145 tell 121.73.101.49, length 28
11:56:22.177828 ARP, Request who-has 203.97.30.144 tell 121.73.101.49, length 28
11:56:22.177857 ARP, Request who-has 203.97.30.145 tell 121.73.101.49, length 28
11:56:23.177824 ARP, Request who-has 203.97.30.144 tell 121.73.101.49, length 28
11:56:23.177844 ARP, Request who-has 203.97.30.145 tell 121.73.101.49, length 28
11:56:28.361837 ARP, Request who-has 203.97.30.144 tell 121.73.101.49, length 28
11:56:28.361868 ARP, Request who-has 203.97.30.145 tell 121.73.101.49, length 28
11:56:29.361839 ARP, Request
```

---

### Post by grahammechanical on 2010-12-29
I am not an expert. I am mystified by that listing, but I do see a pattern. There are three addresses that are being connected to again and again. The action seems to be to get information about these addresses and send the information to variation of the address. Note "Request who-has" and "tell."

I would say that your friend's computer has been infected with a trojan program that is being use to block access to these three sites by repeated asking them for information and them re-sending the information back to the sites.

Of course I could be completely wrong.

Regards.

---

### Post by Bucky Ball on 2010-12-29
You might want to try asking this question on a Linux-Mint forum, if that is the OS you are talking about. You might have more success ...

Perhaps ports open somewhere. 

Grahammechanical: Trojans don't really exist in Linux.

---

### Post by BurningSludge on 2010-12-29
Could your friend be using bit-torrent?

---

### Post by ljhffmn on 2010-12-29
Where is your friend getting his internet from? This appears to be  typical Address Resolution Protocol behavior (that's the ARP in those packets.) I'm no expert and my only real reason for making this suggestion is that while in an undeveloped country I was purchasing internet from a rather shady person so I would at least once a week leave an instance of iptraf or WireShark running and log all activity to ensure he wasn't talking to my machine. When I'd have a grep through the logs You'd see that the hundreds of computers on this system were constantly sending these ARPs. It's how the computers on certain networks resolve MAC address from the given IPV4 Addresses. This can be a security concern as tools like arpspoof can be utilized to instigate a man-in-the-middle attack. I would:

Prefix: Study up on ARP RARP and man-in-the-middle, here are some links... 
[http://en.wikipedia.org/wiki/Address_Resolution_Protocol]("http://en.wikipedia.org/wiki/Address_Resolution_Protocol")
[http://tools.ietf.org/html/rfc826]("http://tools.ietf.org/html/rfc826")
[http://en.wikipedia.org/wiki/ARP_spoofing]("http://en.wikipedia.org/wiki/ARP_spoofing")

1st: Use my newly obtained knowledge to check the problematic machine to see that it's not punching out ARP for no reason (perhaps the protocol is on some kind of IPX/SPX compatible thing {like I said I'm no expert}).

2nd: Check any other networked equipment on the same segment of the network as the problem machine to ensure that they're not on an ARP producing protocol.

One and two have eliminated it being your fault and caused you to learn things :)

3rd: Call the cable company and ask if they have ARP turned on. This level of ARP traffic on their end could be indicative of an improper configuration.

I hope this helps. Let us know what you find out.

---

### Post by WarrenL on 2010-12-29
Hi folks,

Thanks for the replies so far.

Firstly, Bucky Ball:

> **Bucky Ball said:**
> You might want to try asking this question on a Linux-Mint forum, if that is the OS you are talking about. You might have more success ...

There's a mix of Ubuntu and Mint in the computers I look after for people (not to mention Windows). I usually have more success getting answers from the Ubuntu forum since it's more heavily populated, and bearing in mind that Mint is basically Ubuntu with a few tweaks (which in my opinion make it a bit easier on new converts from Windows), it's all relevant.

Now, the computer in question is a simple home setup with a cable broadband connection from a large and reputable nationwide ISP. Shouldn't be any problems there. No torrent programs operating - only Firefox and Thunderbird. We're talking a REALLY basic user here. And the ethernet connection hasn't been monkeyed with by me in any way. It was a case of simply applying the ISP's specified IP, subnet and gateway addresses (remembering that this is cable).

ljhffmn, I'll do the simple things first and put a call through to the ISP. Then I'll study your links. This is all very interesting - in a dozen or so Ubuntu/Mint machines I've never seen anything like it. The distinguishing factor here though is that the machine in question is on a cable connection - all the others use an ADSL router.

---

