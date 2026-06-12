---
title: "Dell Inspiron 15n not working (9.04)"
date: 2009-10-27
forum: Networking &amp; Wireless
---

### Post by samh785 on 2009-10-27
Hello, I just ordered a laptop from dell that had ubuntu preloaded. When I first turned it on, the wireless worked fine. I tried to install karmic on it, and found that the wireless did not work. I reverted it back to the previous install of 9.04 and I am now finding that the wireless is still not working. I'm sort of in panic mode here... The final 9.04 installation seemed to put the proprietary broadcom driver on it automatically, so I assumed it would work. 

Here is the result of "sudo iwlist scan" [B][FONT=Verdana]
[/FONT][/B]```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:1E:2A:54:B3:F6
                    ESSID:"NETGEAR"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:1/5  Signal level:-86 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 02 - Address: 00:25:9C:3B:F5:6F
                    ESSID:"hartley"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:5/5  Signal level:-26 dBm  Noise level:-90 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s

pan0      Interface doesn't support scanning.
```

"hartley" is the network that I want to connect to, and I can see that it can read it when I do that scan so shouldn't it connect?

---

### Post by samh785 on 2009-10-27
Never mind, I simply changed the broadcast settings of the router to 2.412 gigahertz, and it started working

---

