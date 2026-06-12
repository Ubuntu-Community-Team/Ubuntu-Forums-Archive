---
title: "Alpha2 not installing"
date: 2010-07-01
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Yellow Pasque on 2010-07-01
I'm trying to install alpha2 from a usb stick (using uNetbootin), and I'm getting an error about no init. I've verified the md5sum of the .iso, so what have I done wrong? (I hope it's not my USB stick).

---

### Post by go7Ul1ai on 2010-07-01
Have you tried the Startup Disk Creator? That usually works for me. Maybe you could try burning the image to a CD? Though it is so slow when you're used to USB ^_^

---

### Post by Yellow Pasque on 2010-07-01
Thanks for the reply, but I've decided to try the alternate installer. I don't want to waste a CD on a partition that's mainly for experimenting. If I really have to, I'll install Lucid and upgrade :\

---

### Post by andrewabc on 2010-07-01
cd-rw make testing with CD much easier. Buy a 10 pack of cd-rw and you can burn all the different ubuntu versions(ubuntu/kubuntu/xubuntu/lubuntu, 32/64 bit, alternate, alphas/betas) in case you ever need them. And then you can make livusb from them as well in case you don't have lots of hard drive room, or a old computer doesn't accept liveusb.

---

### Post by Yellow Pasque on 2010-07-01
Hmm. I guess I could use a CD-RW (I have them).. I hate all that noise from the CD drive though. The USB install is just so fast and quiet when it works. Good tip, though (thanks).

---

### Post by psyke83 on 2010-07-01
> **Temüjin said:**
> Thanks for the reply, but I've decided to try the alternate installer. I don't want to waste a CD on a partition that's mainly for experimenting. If I really have to, I'll install Lucid and upgrade :\
If you're using the alternate image from a USB drive, you probably need to add this to the kernel boot line:
```
cdrom-detect/try-usb=true
```...unless the installer has been changed to enable this automatically.

---

### Post by andrewabc on 2010-07-01
question for those who install from usb.
Is there still the problem that it confuses usb with cd-rom if installed via liveusb?
I assume that was fixed a long time ago. I test with liveusb, but always install with livecd since I wasn't sure if that bug was fixed.

---

### Post by Yellow Pasque on 2010-07-01
Well, my issue is solved using psyke83's boot flag (thx).
@andrew, I've never had that issue and I've done my last 5 or so ubuntu/debian installs via USB.

---

### Post by RudElph on 2010-07-03
I still can't boot from LiveUSB Maverick ubuntu-netbook.

---

