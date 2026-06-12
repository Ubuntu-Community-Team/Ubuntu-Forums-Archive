---
title: "Problem Geforce 7300gt"
date: 2008-04-22
forum: Multimedia Software
---

### Post by Aarrox on 2008-04-22
Problems with XFX Geforce 7300GT
When i was trying to star Ubuntu with the live CD i got this message:

"[ 0.424000] ..MP-BIOS bug:8254 timer not connected to IO-APIC¨

[ 0.424000] Kernel panic- not spyncing: IO-APIC timer doesn't work! Boot with apic=debug and send a report. Then try booting with 'noapic' option"

Then i created a virtual machine with Vmware, and i figured that without VGA it works so i think it is the Geforce 7300GT.

If someone could help me with this problem, maybe is another thing, i dont know xD.

Thx!

---

### Post by phidia on 2008-04-22
What version of ubuntu are you trying to run? You should be able to start in safe or low graphics mode and then try to get the nv driver loaded.
If you can get to the commandline from your livecd (Alt+Ctrl+F1) you can type
> dpkg-reconfigure xserver-xorg then select the correct (nv) driver plus select your monitor settings.

---

### Post by jlh68 on 2008-04-23
I did not have any problem with my 7300GT using 8.04 Beta.  The software actually took me through the driver installation.

---

### Post by cooke77 on 2008-08-19
I use a nVidia GeForce 7300GS (256 Mb).
It works, in both Ubuntu 8.04 LTS, and Kubuntu 8.02 LTS.
Never have to install nVidia's 'restricted drivers', why?
Graphics-card works, so there is no need to 'configure' it.
I think you've fallen into the common trap most Linux-users fall into...and, that's 'you have to configure everything!'.
With some apps, you don't have to, because there is simply no need to.
Go by the old saying..... "If it ain't broke, don't try to fix it!"

---

