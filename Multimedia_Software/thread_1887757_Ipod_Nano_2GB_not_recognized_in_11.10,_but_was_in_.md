---
title: "Ipod Nano 2GB not recognized in 11.10, but was in 11.04"
date: 2011-11-27
forum: Multimedia Software
---

### Post by Statik on 2011-11-27
Hi all,
I have an ipod nano 2gig that my son uses. It used to be recognized in 11.04 but now does not even show in dmesg when plugged in. It charges fine from USB, but is not in any way recognized. I have tried installing the libimobiledevice-utils and such as recommended in several threads. 

Am I facing a hardware (bad cable) or a software issue here?

Thanks!

Statik

---

### Post by hansdown on 2011-11-27
Hi, Statik.

Are you able to see it in banshee?

---

### Post by Statik on 2011-11-27
I'm not able to see it in any program, nor does the ipod switch over to the 'do not disconnect' screen it usually presents. Its like there isn't any data connection made.

Statik

---

### Post by hansdown on 2011-11-27
I'm not sure, if

```
gtkpod
```

works with the nano.

Give it a try.

---

### Post by Statik on 2011-11-28
I've already tried that as well. I'm starting to suspect the USB cable if no one has had trouble with their ipod nano's with 11.10.

Statik

---

### Post by Statik on 2011-11-29
So, I bought a new cable for the ipod. This did not solve the problem. Then I tried the ipod on a few other computers. It was also not recognized. So, I researched that problem and found that I should reboot the ipod (hold menu and center button until the apple logo appears). This fixed the problem. The ipod was recognized in 11.10 as before.

Thanks!

Statik

---

### Post by hansdown on 2011-11-30
Glad you fixed it, Statik.

---

### Post by gordintoronto on 2011-11-30
How about if you connect the cable with the ipod off, then turn it on? That's the approach I always use with cameras.

---

