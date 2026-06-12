---
title: "Connection is established but not able to connect to internet in Ubuntu 11.04"
date: 2011-05-21
forum: Networking &amp; Wireless
---

### Post by vvishnu.thota on 2011-05-21
Hi
I bought my new Dell inspiron N1401 64bit laptop. It has windows 7 installed in it, I am begineer to linux. I have installed Ubuntu 11.04 64 bit version. I have a wired internet connection which works fine with my windows 7. When I switch to Ubuntu, when internet cable is plugged, the top right corner, network manager shows connection is established, but when I open firefox I cannot access internet. I tried searching on forums, but I could not make it work. If I type ifconfig command in terminal attached is the output I get, I dont know what is the problem. Please help me in this, as I want to use Ubuntu than Windows

---

### Post by sanderj on 2011-05-21
Your ifconfig looks good. Run two commands to find out what's going, and post the output here:

Commands:

```
mtr -n 8.8.8.8 --report -c4
mtr nu.nl --report -c4

```

My output:

```
sander@R540:~$ mtr -n 8.8.8.8 --report -c4
HOST: R540                        Loss%   Snt   Last   Avg  Best  Wrst StDev
  1.|-- 192.168.1.254              0.0%     4    2.2   2.7   2.1   4.1   0.9
  2.|-- 82.169.27.254              0.0%     4   24.4  24.6  21.6  30.8   4.3
  3.|-- 195.69.144.247             0.0%     4   24.4  41.2  23.7  92.0  33.9
  4.|-- 209.85.248.88              0.0%     4   23.6  24.2  23.6  25.3   0.8
  5.|-- 216.239.49.28              0.0%     4   26.6  29.5  26.6  36.5   4.7
    |  `|-- 216.239.49.30
  6.|-- 209.85.255.122             0.0%     4   38.3  30.9  26.6  38.3   5.4
    |  `|-- 209.85.255.118
  7.|-- 8.8.8.8                    0.0%     4   27.6  35.7  27.6  58.6  15.3


sander@R540:~$ mtr nu.nl --report -c4
HOST: R540                        Loss%   Snt   Last   Avg  Best  Wrst StDev
  1.|-- 192.168.1.254              0.0%     4    2.9   2.5   2.1   2.9   0.4
  2.|-- 82-169-27-254.ip.telfort.  0.0%     4   21.0  21.0  20.3  21.4   0.5
  3.|-- po1.ccr01.ams03.atlas.cog  0.0%     4   23.5  23.2  22.3  23.6   0.6
  4.|-- dedigate-nv.demarc.cogent  0.0%     4   22.6  23.1  22.6  23.9   0.6
  5.|-- t9-3.gw1.ams2.terremark.n  0.0%     4   24.0  23.9  23.0  25.4   1.1
  6.|-- ???                       100.0     4    0.0   0.0   0.0   0.0   0.0
  7.|-- 62.69.179.198              0.0%     4   35.3  27.0  23.4  35.3   5.6
sander@R540:~$ 

```

---

### Post by prshah on 2011-05-21
> **vvishnu.thota said:**
> when internet cable is plugged, the top right corner, network manager shows connection is established, 

ifconfig command in terminal attached is the output I get,

Have you manually setup your IP Address? I don't think your computer should get an IP address of 192.168.1._**[size="2"]1[/size]**_, under normal, standard DHCP setup (not impossible, but improbable).

Please give more information about how you connect to Internet in Windows? Can you also post the output to ```
ipconfig /all
``` from Windows (when connected)?

---

