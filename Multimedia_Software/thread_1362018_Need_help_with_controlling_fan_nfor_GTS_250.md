---
title: "Need help with controlling fan nfor GTS 250"
date: 2009-12-22
forum: Multimedia Software
---

### Post by darkhalo on 2009-12-22
I recently upgrade my video card to a PNY Nvidia GTS 250. I'm running dual boot of windows and ubuntu 9.04. It seems that under windows, the Nvidia driver can control the fan noise very well, however, the fan is running 100% speed under ubuntu, and the noise level is unbearable. Except for installing a fan controller which cost about $50 since the GTS 250 fan connector is 4-pin not 3-pin, does anyone know a solution to this problem?

---

### Post by Qola on 2009-12-22
Have you tried nvclock?

Try this command if you haven't.

```
sudo aptitude install nvclock && nvclock -f -F 60
```

---

### Post by RedSingularity on 2009-12-22
Have you installed the proper drivers?  I have the same card and it is VERY noisy if i take out the drivers.

---

### Post by VertexPusher on 2009-12-22
I have the same card, and yes, the Nvidia driver is required for fan control. The driver is available through "System --> Administration --> Hardware Drivers". Installing it takes a few clicks and one system restart.

---

### Post by darkhalo on 2009-12-22
> **Qola said:**
> Have you tried nvclock?

Try this command if you haven't.

```
sudo aptitude install nvclock && nvclock -f -F 60
```

I tried nvclock, it tells me that my card doesn't support fanspeed adjustments

---

### Post by Qola on 2009-12-22
> **darkhalo said:**
> I tried nvclock, it tells me that my card doesn't support fanspeed adjustments

Fair enough. I think I remember reading that if you add coolbits in xorg.conf that you can alter the fan speed, but I don't know if that's 100% true as I always use nvclock.

---

### Post by darkhalo on 2009-12-22
> **VertexPusher said:**
> I have the same card, and yes, the Nvidia driver is required for fan control. The driver is available through "System --> Administration --> Hardware Drivers". Installing it takes a few clicks and one system restart.

do you use the version 180 driver that ubuntu supplies, or the one that Nvidia's website supplies, which is 190.54?

---

### Post by Qola on 2009-12-22
Nvidia's 190.53.

---

### Post by darkhalo on 2009-12-22
190.53 seem to do it, although it still makes more noise than under windows, it's bearable. thanks for u guys' help. glad that I change from ATI with Nvidia's driver support.

---

### Post by VertexPusher on 2009-12-23
> **darkhalo said:**
> do you use the version 180 driver that ubuntu supplies, or the one that Nvidia's website supplies, which is 190.54?
I'm using the one supplied by Ubuntu. As soon as it is loaded, the fans slow down and become almost inaudible. I hear them only during startup and shutdown, i.e. before the driver is loaded and after it is unloaded. That's perfectly normal.

I did not install anything manually from Nvidia's website.

---

### Post by darkhalo on 2009-12-23
I don't know why the one that ubuntu supplies doesn't work for me, which is the reason I made this post. Now I just went on installing the 190.54 instead. big improvement with this driver, still a little bit noisy compared to under windows, but this card runs hot, even when idle, its temp is 51C, so the fan is running at 27%. Anyway, I'm happy now. Thanks again.

---

### Post by jantz on 2010-06-26
This maybe a bit of a necro of this thread, but i'm seeing the same problem.

xx@xx:~$ sudo nvclock -f -F 60
Unhandled init script entry with id '&#65533;' at c758
Error: Your card doesn't support fanspeed adjustments!


Running 10.04 and  195.36 drivers. I can see that on Nvidia site the drivers are up to like, 256.35?? are those correct?

regards
John

---

