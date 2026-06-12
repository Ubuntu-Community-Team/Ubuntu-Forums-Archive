---
title: "D-Link DWA-140 not working in 11.04"
date: 2011-04-28
forum: Networking &amp; Wireless
---

### Post by Linxguy on 2011-04-28
It worked in 10.10. What's up?

---

### Post by MooPi on 2011-04-28
Details are needed for "Whats up" requests.
Type of device, connection type, what have you attempted to do to correct ? etc........

---

### Post by karbo on 2011-04-28
Having the same problem. Just upgraded to 11.04 and my D-Link DWA-140 stopped working. Network applet in the panel says "device not ready (firmware missing)"

Anyone knows how to get the proper driver for Ubuntu 11.04?

---

### Post by elf23 on 2011-04-29
I just tried this and it works. Phew!

[http://askubuntu.com/questions/34742/how-do-i-get-a-d-link-dwa-140-usb-wlan-working](http://askubuntu.com/questions/34742/how-do-i-get-a-d-link-dwa-140-usb-wlan-working)

---

### Post by myromance123 on 2011-05-08
I cannot believe the solution is so simple!
Thank you so much elf23!

I  can confirm this is the same problem experienced on my Kubuntu and Ubuntu 11.04 systems.

```
lsmod | grep rt
```

returned for me :

```
ismail@AMD-Home:~/Documents/2010_0709_RT2870_Linux_STA_v2.4.0.1$ lsmod | grep rt
parport_pc             36959  0 
parport                46458  3 parport_pc,ppdev,lp

```

Thus I was able to skip removing anything starting with rt and the blacklisting part.
I just went straight and did:
```
sudo modprobe rt2870sta

```

I can't explain how happy this makes me :D I was struggling with the Dlink and Ralink drivers and constantly experiencing make error 2 problems. Thanks once again for sharing this valuable information.

---

### Post by Linxguy on 2011-05-16
Thank you Elf. Going to try it now. :)

Edit: Thanks that worked great! :)

---

