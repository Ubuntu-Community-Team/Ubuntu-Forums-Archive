---
title: "Yet another rt2500 low bandwidth thread"
date: 2009-06-10
forum: Networking &amp; Wireless
---

### Post by lots_of_entropy on 2009-06-10
Following problem:

I have a RaLink RT2500 based PCI wifi card (WPA PSK) on Jaunty that initially works fine. However, after some time the bandwidth drops to about 0.6Mb/s. 

I had the same problem in Intrepid and used the serialmonkey CVS driver that worked ok. However, that driver does not work with the new kernel that comes with Jaunty. So I am stuck with the stock driver.

Funny thing is, if I do a 

```

ifconfig wlan0 down
iwconfig wlan0 rate 54M

```

and reconnect, the bandwidth is normal for some time and then drops again. 

Ndiswrapper does not work very well either (bad reception, random disconnects) and I prefer the open sourced driver anyways.

So the fact that it used to work with the serialmonkey driver rules out a hardware problem. I guess some bug in the ubuntu kernel driver's rate control.

Any suggestions from you wizards of OS out there?

P.S: logs are clean

---

