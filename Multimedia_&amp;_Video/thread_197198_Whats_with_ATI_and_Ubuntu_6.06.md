---
title: "Whats with ATI and Ubuntu 6.06?"
date: 2006-06-15
forum: Multimedia &amp; Video
---

### Post by BuffaloX on 2006-06-15
Sorry for dobbelt post, I got message that it was out of date or something other error...

ATI Radeon 9800 (R350), AGP, Athlon 64 CPU, SIS AGP

ATI works fine with both 2D and 3D in AMD64 Ubuntu alternate. :D
glxgears about 6400 fps.

But the 32 bit version dosn't work with 3D.
I have tried sooo many things, including raw install from both Desktop and alternate CD's. Even making my own .deb package. Checked status of AGP port driver. Standard method just installing via synaptic. Just about every guide to be found in this forum plus official guides.

I have had about 8 different methods of "succesful" installs, but everytime, no 3D acceleration only mesa.

Does your 3D work with ATI?
Which ATI card?
Is your system PCI/AGP/PCI-express
Is your system 32 or 64 bit (which CPU)
Which Ubuntu do you use. 32/64 desktop/alternate

---

### Post by nephesh on 2006-06-15
I have a Radeon 9800 pro, on an Opteron running in 32bit and it works fine.

I use this guide and it works 100% of the time for me.

[http://ubuntuforums.org/showthread.php?t=143283&highlight=ati+driver](http://ubuntuforums.org/showthread.php?t=143283&highlight=ati+driver)

---

### Post by SteinbergerNate on 2006-06-15
You're having trouble as well. I wish I could figure out what is going on. I finally got it working yesterday after replacing libGL.so.1.2 and then there was an update this morning and it must have messed it up because I can't get it to work at all.

---

### Post by BuffaloX on 2006-06-15
-> Nephesh. Thanx I never saw that guide, Ill try it now.
What is your chipset please? Which Ubuntu breezy or dapper?

-> SteinbergerNate. Sorry to hear, what is your erhh... everything. :-)

---

### Post by SteinbergerNate on 2006-06-15
Radeon R250 Lf [FireGL 9000]
Using 32 bit Dapper on Dell Inspiron 600m
Looks like the system is reporting that it's AGP but I can't tell for sure since it's a laptop.

---

### Post by SteinbergerNate on 2006-06-15
Ok, so I just put my fglrx driver back into xorg.conf and restarted. Looked in the ATI control panel, and it said that OpenGL was unavailable.

---

### Post by BuffaloX on 2006-06-15
Tried the guide pointed to by nephesh, couldn't make it work...:-( 

I hoped to get some statistics about which systems work with what, too often people don't write information about distro and platform, just "great worked for me" or "didn't work..."

-> Nephesh Sorry obviously you use Dapper.

-> SteinbergerNate: I read there is problems with Radeon below 300.
I guess your right it's AGP, and Intel chipset, Pentium mobile.

---

### Post by BuffaloX on 2006-06-16
Well enough is enough...
Ordered an nvidea, and hope it works better... :-$

---

