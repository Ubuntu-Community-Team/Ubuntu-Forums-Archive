---
title: "Attempted network bridge, now I can't connect to the internet"
date: 2009-07-28
forum: Networking &amp; Wireless
---

### Post by wrhalste on 2009-07-28
I recently got an Xbox 360 and I didn't want to pay for a wireless adapter. I tried bridging the connection on my laptop via wireless-laptop-ethernet-xbox. I managed to screw up something so that now my laptop can't connect by wireless or ethernet. Now I just want to reset my network settings and get internet back.

Let me know if you need any info to help diagnose the problem. Any help is very much appreciated.

---

### Post by Iowan on 2009-07-28
What's in */etc/network/interfaces*?

---

### Post by wrhalste on 2009-07-28
Actually I managed to figure it out. All I needed to do was type "ifconfig eth0 192.168.1.254" and "ifconfig wlan0 192.168.1.254" in a root terminal. I had changed them while trying to make the bridge. I still have no idea how to bridge the connection but I'm not going to try it again.

Thanks anyway though. I appreciate it.

---

### Post by Iowan on 2009-07-29
Having both interfaces assigned the same address seems more like a problem than a cure...But can't argue with success.  Next question will be if it stays fixed after next reboot...

---

### Post by wrhalste on 2009-07-29
It's still working and I have turned off my computer twice. What problems could arise from having the interfaces set to the same address?

---

### Post by Iowan on 2009-07-30
Ordinarily (at least on previous versions) having two interfaces with same address would either confuse routing - or throw an addressing error. Perhaps your connection bridging worked better than you thought...

---

