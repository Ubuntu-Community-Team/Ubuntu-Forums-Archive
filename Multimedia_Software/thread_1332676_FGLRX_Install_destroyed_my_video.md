---
title: "FGLRX Install destroyed my video"
date: 2009-11-20
forum: Multimedia Software
---

### Post by TUOggy on 2009-11-20
Okay, I'm trying to get OpenGL to work on my computer, so I read that I needed to install the fglrx drivers.

I have an ATI Radeon 9200.  I went through synaptic to install the drivers.  After that, my video was messed up.  I got a split screen with the bottom being static, and the top being two instances of the ubuntu logo.

So, I tried to log in through repair mode.  Tried the X repair.  Didn't work.  Tried setting xorg.conf back to defaults... didn't work.  Then even tried removing fglrx using:

```

sudo dkms remove -m fglrx -v 8.600 --all

```

and I am still getting the same thing...  What do I need to do to get my video setting set back to default?

---

### Post by TUOggy on 2009-11-20
Okay, after a night of searching and futile attempts, I finally found this

```

sudo apt-get remove xorg-driver-fglrx

```

immediately followed up with

```

sudo apt-get purge xorg-driver-fglrx

```

That finally fixed the system

---

### Post by xzero1 on 2009-11-20
Boot into recovery mode then try:

```
back up and remove xorg.conf
dpkg -reconfigure -phigh xserver-xorg
aptitude purge xorg-driver-fglrx

```reboot and you should be back to your default driver.

---

