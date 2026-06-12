---
title: "Restarting after Kismet"
date: 2009-04-10
forum: Networking &amp; Wireless
---

### Post by Whisp3r on 2009-04-10
Hi everyone.

Can someone tell me what I'm doing wrong after firing up Kismet? I fire up Kismet with my Intel3945, scan around, and then quit. It gives an error of "Segmentation fault." as it exits to terminal.

I set my card via 'ifconfig wlan0 mode managed' back to managed, and it reads as such under iwlist. However, my Intel card can't connect obtain a new IP from a wireless network it appears. DHCP Discover just runs, and run, and eventually says no DHCPOFFERS received...

Thanks!

---

### Post by Alias1407 on 2009-04-10
Same problem happens with me,

I have the Intel4965 so i'm not sure how much this will differ do you use,

```
sudo airmon-ng start wlan0
```

this should say that mon0 interface has started.

Then you can start up kismet, when you shutdown kismet you should be able to go...

```
sudo airmon-ng stop mon0
```

And the command works however I cannot connect back to any other network,

Usually I just restart     :-?

---

### Post by Whisp3r on 2009-04-10
I'm stumped. I've tried restarting network services, running dhclient, etc. The cards its in managed mode, and even associates with the point, but just can't seem to catch the IP.

---

### Post by Whisp3r on 2009-04-11
Hooray, I figured it out.

You need to modprobe your wireless drive out (modprobe -r iwl3945, in my case), and then modprobe it back in. That solves this problem, at least with my card! Hooray!

---

