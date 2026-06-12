---
title: "How can I configure xserver to vesa?"
date: 2007-10-28
forum: Multimedia &amp; Video
---

### Post by gubemton on 2007-10-28
I've recently installed 4.10 and had to boot the CD in "safe graphics mode". However, post-installation, the display is screwed and I need to change the xserver settings to vesa. I've run dpkg-reconfigure xserver-xorg a few times, but without success. If someone could point me at a guide to setting up xserver to the equivalent of the live CD's "safe graphics mode" option, I'd be grateful. 

Specs, btw, are these:

Dell Optiplex GXa
Intel P2-233 CPU
192MB RAM
S3 Savage4 video card
AcerView 34eL monitor
4Gb bootdrive
6Gb second drive

---

### Post by taurus on 2007-10-28
Boot into recovery mode from GRUB menu.  At the prompt, run

```
nano -Bw /etc/X11/xorg.conf
```
Scroll down until you get to the Driver section.  Change the video driver from whatever it is right now to **vesa**.  Save it with <Ctrl>o and exit with <Ctrl>x.  Then, reboot.

```
shutdown -r now
```

---

### Post by kerry_s on 2007-10-28
4.10?

for those specs->
[http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-xfce-CD-1.iso)

---

### Post by gubemton on 2007-10-28
> **taurus said:**
> Boot into recovery mode from GRUB menu.  At the prompt, run

```
nano -Bw /etc/X11/xorg.conf
```
Scroll down until you get to the Driver section.  Change the video driver from whatever it is right now to **vesa**.  Save it with <Ctrl>o and exit with <Ctrl>x.  Then, reboot.

```
shutdown -r now
```

Thanks :-)

---

### Post by gubemton on 2007-10-28
> **kerry_s said:**
> 4.10?

That's me getting confused between 7.04 and 7.10 and compromising with a typo :-)

> for those specs->
[http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-xfce-CD-1.iso)
I tried xubuntu, but didn't even get to the splash screen; edubuntu 7.10 *very nearly* worked, but I now seem to have lost the hard disks.

I'll have a fiddle to see if I can get the disks to appear again, and then I might have a go at reformatting the boot drive with a DOS floppy and the format utility. 

I'm downloading the xfce image because I'd like to see what it's like, but as the target PC is for children, I thought edubuntu looked nice so I'll stick with that if I can. Thanks for the link though :-)

---

### Post by kerry_s on 2007-10-28
> **gubemton said:**
> That's me getting confused between 7.04 and 7.10 and compromising with a typo :-)


I tried xubuntu, but didn't even get to the splash screen; edubuntu 7.10 *very nearly* worked, but I now seem to have lost the hard disks.

I'll have a fiddle to see if I can get the disks to appear again, and then I might have a go at reformatting the boot drive with a DOS floppy and the format utility. 

I'm downloading the xfce image because I'd like to see what it's like, but as the target PC is for children, I thought edubuntu looked nice so I'll stick with that if I can. Thanks for the link though :-)

xubuntu is bloated. debian is way better on older low resource systems. once you get use to using debian you can go custom install and build it more resource friendly. 

my laptops a 450mhz 256ram, i do a debian dase install and build up from there, nothing on my system is slow. :)

---

