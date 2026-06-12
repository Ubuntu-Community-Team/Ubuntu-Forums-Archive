---
title: "very slow internet on ubuntu [jaunty]"
date: 2009-05-06
forum: Networking &amp; Wireless
---

### Post by zettel on 2009-05-06
hello all.

i just installed ubuntu a few days ago and have been scouring the internet for solutions to my problem. i have never used linux before and am getting very low internet speeds. i followed someone's instructions on this board and removed network manager and installed wicd network manager but that did not help. i'm on a wireless connection [verizon] and all other computers [there are 3] are working fine with reasonable download speed. before this i was using xp and the internet was working fine. what can i do to fix my internet speed? i'm at a complete loss.

thanks for reading.

---

### Post by modmadmike on 2009-05-06
> **zettel said:**
> hello all.

i just installed ubuntu a few days ago and have been scouring the internet for solutions to my problem. i have never used linux before and am getting very low internet speeds. i followed someone's instructions on this board and removed network manager and installed wicd network manager but that did not help. i'm on a wireless connection [verizon] and all other computers [there are 3] are working fine with reasonable download speed. before this i was using xp and the internet was working fine. what can i do to fix my internet speed? i'm at a complete loss.

thanks for reading.

run this in Applications>Accessories>Terminal and post the output:
```
lspci | grep "Wireless"
```

---

### Post by zettel on 2009-05-06
i'm afraid copy/pasting that on terminal yields nothing. is there something missing in that command perhaps?

---

### Post by anlayne on 2009-05-07
I'm not the original poster, but I'm having the same problem.

Here is the output of lspci | grep "Wireless":

```
03:00.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)
```

I'm using a D-Link DWA-556 to connect to a D-Link DIR-615-SW.

Under Hardy with Wicd I had no problems, but now I'm using 64-bit Jaunty with network-manager and having big problems.

Thanks.

---

### Post by zettel on 2009-05-10
i just installed an older version and didn't need to do anything. internet works fine.

---

### Post by enathanson on 2009-07-23
Try setting the mtu down to 1492 for your wireless interface (default is 1500).  Use the ifconfig command and scroll down to wlan0 to look for current mtu (likely 1500).  To set it to 1492, type the following:
   sudo ifconfig wlan0 mtu 1492
Why this works?  I have no idea.  Credits to Odeno in Intrepid thread on same subject:
   [http://ubuntuforums.org/archive/index.php/t-969256.html](http://ubuntuforums.org/archive/index.php/t-969256.html) (search for 1492 to find his/her suggestion)

---

### Post by simon@syd on 2009-07-30
I had a similar problem - i posted the solution to my problem here:
[http://ubuntuforums.org/showthread.php?t=1227509](http://ubuntuforums.org/showthread.php?t=1227509)

---

