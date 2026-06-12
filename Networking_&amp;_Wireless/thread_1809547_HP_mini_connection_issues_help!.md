---
title: "HP mini connection issues help!"
date: 2011-07-21
forum: Networking &amp; Wireless
---

### Post by yumkiffs on 2011-07-21
Hi,
I recently decided to install Ubuntu 11.04 on an old HP mini 1100 I have and it works fine EXCEPT I can't connect to the internet! No wireless or wired connections are working so I think it's a driver issue but tbh I'm pretty new to all this and don't have that much knowledge of what I'm doing haha The wireless also says "wireless disabled by hardware switch" in the menu but the switch (a little toggle on the front) doesn't do anything. I've already rfkill unblocked everything yet nothing works :( any help would be awesome!

oh my wireless card is a broadcom BCM4312, and the reason I haven't at least installed wired drivers is because I don't know how to do that without the internet...

---

### Post by mikewhatever on 2011-07-21
You can try installing the STA wireless driver for the BCM4312 from the installation media. It's not a point and click precess, but, it's doable.
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA%20-%20No%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA%20-%20No%20Internet%20access)

---

### Post by yumkiffs on 2011-07-21
Hi thanks for helping :D That kinda worked, the light on the wireless switch is blue now not red, except it still says "wireless disabled by hardware switch" in the menu. I've tried pretty much every solution on here and downloaded all sorts of drivers and things onto a usb then installed them that way, but nothing seems to work...

---

### Post by nm_geo on 2011-07-21
yum run this 

```
lsmod
```

paste results

```
rfkill list all 
```

I know you are sure the manual wireless switch is in the correct position.

---

### Post by yumkiffs on 2011-07-21
Yes I'm sure the switch is in the right position haha fair call though. Anyway it seems one of the many things I blindly (and potentially stupidly) installed has started doing its thing, I'm connected now. Not sure what happened but I think it was that link Mikewhatever gave me, so uhh, thanks for the help! 

...I realise I'm probably far too cabbage with computers to be playing around with this. But I'll learn!

---

### Post by mikewhatever on 2011-07-22
Hey, glad you solved it. I really wish Broadcom drivers were included by default. It would save so much headache.

---

