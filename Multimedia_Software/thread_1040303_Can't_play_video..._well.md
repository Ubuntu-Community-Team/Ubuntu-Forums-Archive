---
title: "Can't play video... well"
date: 2009-01-15
forum: Multimedia Software
---

### Post by frost151n on 2009-01-15
Hello,

When i switch to fulscreen mode the video becomes jerky, sluggish. And the same video plays smooth in small window size.

I have gstreamer-properties set to X Window System (No Xv)

I tried VLC, Totem, MPlayer. Same problem in each of them.

...this is the only reason I boot into Vista.:cry:

I have an ATI HD 3850 512MB Sapphire make and a BenQ E2200HD display.

---

### Post by Twitch6000 on 2009-01-15
> **frost151n said:**
> Hello,

When i switch to fulscreen mode the video becomes jerky, sluggish. And the same video plays smooth in small window size.

I have gstreamer-properties set to X Window System (No Xv)

I tried VLC, Totem, MPlayer. Same problem in each of them.

...this is the only reason I boot into Vista.:cry:

I have an ATI HD 3850 512MB Sapphire make and a BenQ E2200HD display.

My brother had the same problems too before he used VLC and installed libdvdscss.

I suggest you go into the package manager and install libdvdcss from there.

Or if you like using the terminal copy and paste this into the terminal - 

```
 sudo apt-get install libdvdss 
```

This should fix your problems :).

---

### Post by frost151n on 2009-01-15
It couldn't find it!!!

```
frost@Maaz-U:~$ sudo apt-get install libdvdss
[sudo] password for frost: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libdvdss
frost@Maaz-U:~$ 

```

Should mention that I'm on Ibex

---

