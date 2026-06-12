---
title: "Unable to connect with Dlink PCI adapter"
date: 2012-04-20
forum: Networking &amp; Wireless
---

### Post by debd on 2012-04-20
The problem is a little odd itself.
I have a dlink DFE-520TX PCI LAN adapter which is currently recognised as eth1 in my Ubuntu box. The driver used is VIA Rhine III and it was working all fine.

Just a day before I noticed, I couldn't connect to the internet,  I can connect to the gateway my ISP provides, network applet shows connected. But ping results are mostly RTOs.. initially it seemed like a problem with the ISP but the same problem happened in my Arch install.

So, I booted into windows and saw the network was working. I could surf internet. I did this quite a few times- boot into linux, try pinging the gateway with mostly RTOs and then back into windows with a working connection. So, probably my ISP isn't bluffing with me.

Although in windows, there's another problem - sometimes the network icon in the taskbar very freqently shows disconnected and back on. So, I opened the chesis, refitted the LAN card and still nothing.

ifconfig recognises both my onboard (eth0, dysfunctional) LAN adapter and the pci one. I tried disabling eth0 which solved nothing. 

Could it be a hardware problem?

---

### Post by sanderj on 2012-04-20
"mtr -n 8.8.8.8" is a nice command to see what's going on.

Or use teh command below to get a report


```
sander@R540:~$ mtr -r -c10 -n 8.8.8.8
HOST: R540                        Loss%   Snt   Last   Avg  Best  Wrst StDev
  1.|-- 192.168.1.254              0.0%    10    1.9   2.9   1.8   6.7   1.7
  2.|-- 82.170.147.254             0.0%    10   19.5  23.5  19.3  56.5  11.6
  3.|-- 195.69.145.100             0.0%    10   21.6  23.0  21.6  24.9   1.0
  4.|-- 209.85.254.90              0.0%    10   79.7  36.6  21.7  90.2  26.3
  5.|-- 209.85.255.70              0.0%    10   23.7  24.0  22.0  28.1   2.2
    |  `|-- 209.85.255.74
  6.|-- 216.239.49.30              0.0%    10   26.0  29.1  25.5  55.5   9.3
    |  `|-- 216.239.49.38
    |   |-- 216.239.49.36
    |   |-- 216.239.49.28
  7.|-- 209.85.255.126             0.0%    10   39.1  32.1  26.0  39.1   4.7
    |  `|-- 209.85.255.130
  8.|-- 8.8.8.8                    0.0%    10   25.8  26.6  25.6  28.0   0.8
sander@R540:~$ 


```

---

### Post by debd on 2012-04-21
Well, seems like the problem was actually with the setup of the local operator.
It's okay now.

Thanks anyway.

---

