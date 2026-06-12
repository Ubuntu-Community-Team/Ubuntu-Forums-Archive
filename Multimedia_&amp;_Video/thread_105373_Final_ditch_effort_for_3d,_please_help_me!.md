---
title: "Final ditch effort for 3d, please help me!"
date: 2005-12-18
forum: Multimedia &amp; Video
---

### Post by Slovak on 2005-12-18
System specs are
Ubuntu 5.10
ATI 9800XT
ASUS TUSL2-C mobo w/intel 815 chipset
1.4Ghz Tualatin processor

I followed [this]("http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide") wiki, both methods 1 and 2 and still get no where.

john@ubuntu:~$ fglrxinfo
display: :0.0 screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

john@ubuntu:~$ modprobe fglrx
john@ubuntu:~$ lsmod | grep fglrx
fglrx 245412 0
agpgart 32328 2 intel_agp,fglrx

john@ubuntu:~$ LIBGL_DEBUG=verbose fglrxinfo
libGL error: XF86DRIQueryDirectRenderingCapable returned false
libGL error: XF86DRIQueryDirectRenderingCapable returned false
display: :0.0 screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

john@ubuntu:~$ grep -R "(EE)" /var/log/Xorg.0.log
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work

What does that mean? My Ubuntu kernel is incompatible? If that's the case then 3d will never work in Ubuntu, right?

My entire Xorg.O.log file is in the attached .zip file

---

### Post by mlomker on 2005-12-18
You'll need to look in /var/log/kern.log and Xorg.0.log for errors.  It sounds like you have a mixture of Breezy's 8.16.20 driver and a newer one installed at the same time.

---

### Post by Slovak on 2005-12-18
I don't understand those logs, can you decipher them for me?
Seems as if there were two drivers loaded, so I removed the ubuntu one as per the wiki. then
I redid everything from method 2 and now all I get is a black screen, no kernel error things anymore once I 
sudo dpkg-reconfigure xserver-xorg from recovery kernel and run.... john@ubuntu:~$ grep -R "(EE)" /var/log/Xorg.0.log 
Driver in xorg.conf says ati, but when I change it to fglrx I black screen all over again.

---

### Post by Slovak on 2005-12-18
Here is my kern.log in the attachment

---

### Post by mlomker on 2005-12-19
[QUOTE=Slovak]Here is my kern.log in the attachment[/QUOTE]

On the last few bootups it was showing 8.20.8, so I'd look in the Xorg.0.log to see if it is trying to set your monitor to an unsupported refresh rate or something like that...

---

