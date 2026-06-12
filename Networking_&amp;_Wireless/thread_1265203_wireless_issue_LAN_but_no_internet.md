---
title: "wireless issue: LAN but no internet"
date: 2009-09-13
forum: Networking &amp; Wireless
---

### Post by tectp on 2009-09-13
Hello Ubuntu community, I have just installed ubuntu and am trying to get on the internet via my wireless router. network manager reports that it is connected, it shows a valik ip address, broadcast address, mask and dns and i can see other computers on my LAN but not the internet. Anyone know where i should start?
thanks, Nick

---

### Post by sanderj on 2009-09-13
First check pure IP connectivity with this mtr command:

```
ubuntu@ubuntu:~$ mtr -n -c 4 -r 20.30.40.50
HOST: ubuntu                      Loss%   Snt   Last   Avg  Best  Wrst StDev
  1. 192.168.2.254                 0.0%     4    3.4   2.1   1.2   3.4   0.9
  2. 192.168.1.254                 0.0%     4    2.9   2.9   2.3   3.8   0.7
  3. 82.169.27.254                 0.0%     4   21.6  29.6  21.0  50.1  13.8
  4. 77.67.64.1                    0.0%     4   53.7  55.3  21.4 124.2  48.4
  5. 64.208.110.165                0.0%     4   26.7  66.3  24.8 161.9  64.9
  6. 208.48.1.198                  0.0%     4  150.5 129.9 107.5 150.5  17.9
  7. ???                          100.0     4    0.0   0.0   0.0   0.0   0.0
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ 

```
If that works, check your DNS with this mtr command:

```
ubuntu@ubuntu:~$ mtr  -c 4 -r ping.xs4all.nl
HOST: ubuntu                      Loss%   Snt   Last   Avg  Best  Wrst StDev
  1. 192.168.2.254                 0.0%     4    2.0   1.8   1.3   2.0   0.3
  2. 192.168.1.254                 0.0%     4    4.5   2.9   2.1   4.5   1.1
  3. 82-169-27-254.ip.telfort.nl   0.0%     4   20.8  37.6  20.7  80.5  28.8
  4. ams-ix.sara.xs4all.net        0.0%     4   23.3  41.8  22.7  74.8  24.6
  5. 0.so-1-0-0.xr4.1d12.xs4all.n  0.0%     4   23.4  59.8  23.4 114.6  39.9
  6. uucp1.xs4all.nl               0.0%     4   49.2  51.9  23.3  95.7  31.1
ubuntu@ubuntu:~$

```

---

