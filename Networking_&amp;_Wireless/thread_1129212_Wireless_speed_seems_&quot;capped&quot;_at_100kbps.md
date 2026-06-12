---
title: "Wireless speed seems &quot;capped&quot; at 100kbps"
date: 2009-04-18
forum: Networking &amp; Wireless
---

### Post by jasbur on 2009-04-18
I'm a long time Ubuntu user. After a "vacation" with OSX Jaunty has brought me back. Anyway, everything went great with the install except my wireless connection is behaving strangely.

I seem to be capped at 100kbps. If I download something from a fast server the download speed tops out at 100kbps +/- I can download the same file on my macbook, using the same wireless network and get ~800kbps. Here is my iwconfig:

```
IEEE 802.11bg  ESSID:"Bleep Bleep Bloop"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:16:01:4A:07:67   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=15/100  Signal level:65/65  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

The link quality seems low but I'm 10 feet from the router. Also I never had any issues on the same hardware running Windows.

---

### Post by hesjnet on 2009-04-18
You said that theese problems don't occur with other operating systems but have you tried to ping a webserver or do a traceroute to se if there is an lag somewhere?

```
ping www.ubuntuforums.org
```

```
sudo apt-get install traceroute
traceroute www.ubuntuforums.org
```

---

### Post by jasbur on 2009-04-18
ping results:

```
--- www.ubuntuforums.org ping statistics ---
100 packets transmitted, 100 received, 0% packet loss, time 99125ms
rtt min/avg/max/mdev = 105.744/179.016/3376.245/407.009 ms, pipe 4

```

traceroute results:

```
traceroute to www.ubuntuforums.org (91.189.94.12), 30 hops max, 60 byte packets
 1  buffalo.setup (192.168.11.1)  19.155 ms  47.991 ms  85.691 ms
 2  76.50.128.1 (76.50.128.1)  96.027 ms  97.349 ms  98.072 ms
 3  gig-2-1.applwi2-rtr2.new.rr.com (24.164.241.21)  98.663 ms  99.371 ms  99.964 ms
 4  srp2-0.gnbywi2-rtr1.new.rr.com (24.164.224.34)  100.684 ms  103.030 ms  103.744 ms
 5  24.94.160.21 (24.94.160.21)  105.090 ms  105.677 ms  109.773 ms
 6  ae-5-0.cr0.chi30.tbone.rr.com (66.109.6.112)  104.248 ms  20.167 ms  14.841 ms
 7  ae-1-0.pr0.chi10.tbone.rr.com (66.109.6.155)  21.774 ms  23.077 ms  22.288 ms
 8  chi-bb1-link.telia.net (213.248.76.97)  24.951 ms  23.533 ms  24.229 ms
 9  nyk-bb1-link.telia.net (80.91.248.193)  42.959 ms  55.517 ms nyk-bb1-pos0-3-0.telia.net (213.248.80.153)  93.725 ms
10  ldn-bb1-link.telia.net (80.91.248.202)  153.440 ms ldn-bb1-link.telia.net (80.91.249.248)  155.379 ms  154.714 ms
11  ldn-b5-link.telia.net (80.91.252.206)  154.044 ms ldn-b5-link.telia.net (80.91.249.178)  156.002 ms ldn-b5-link.telia.net (80.91.252.202)  156.536 ms
12  ldn-tch-i1-link.telia.net (80.91.250.210)  143.123 ms  112.866 ms  108.404 ms
13  113069-ldn-tch-i1.c.telia.net (213.248.74.42)  160.628 ms  161.346 ms  161.938 ms
14  canonical-gw.datahop.net (195.72.130.230)  147.808 ms  150.266 ms  151.585 ms
15  gw0-0-gr.canonical.com (91.189.88.10)  107.969 ms  124.653 ms  141.871 ms
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *
```

---

### Post by jasbur on 2009-04-19
Bump

Does anyone have any ideas?

---

### Post by abdusamed on 2011-02-27
I am facing the same problem as HE is.... on ubuntu 10.04.2. My wirelss seems to be capped too!

---

