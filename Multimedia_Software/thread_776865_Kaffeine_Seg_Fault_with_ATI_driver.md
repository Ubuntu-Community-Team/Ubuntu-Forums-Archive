---
title: "Kaffeine Seg Fault with ATI driver"
date: 2008-05-01
forum: Multimedia Software
---

### Post by jsedwards on 2008-05-01
I have a Dell 530 Inspiron machine that had an nVidia 8300 video card.  If I tried to play any digital video file it would stutter like crazy.  I was using the "nv" driver.  I tried using the "nvidia" driver but could not get that to work at all: [http://ubuntuforums.org/showthread.php?t=764907]("http://ubuntuforums.org/showthread.php?t=764907")

So I went and bought an ATI Radeon 1550 card and put it in.  I installed the xorg-driver-fglrx and got the video working.  However now when I try to run Kaffeine it immediately seg faults with Signal 11.  Since Kaffeine did not seg fault prior to changing to the ATI card I am assuming this must be related to the ATI driver?

Any help debugging this would be most appreciated.

Thanks
  -Scott

---

### Post by jsedwards on 2008-05-01
I forgot to mention that I am still on Kubunut 7.10.  Hopefully, I will have time to backup everything and upgrade to 8.04 in the next few weeks.

---

### Post by jsedwards on 2008-05-01
I uninstalled the restricted driver (apt-get remove xorg-driver-fglrx) and downloaded the driver: ati-driver-installer-8-4-x86.x86_64.run (dated Apr 16th) from the ATI web site.  I made it executable, ran it and it installed perfectly.  Now Kaffeine plays almost all of the videos I have tried (a couple of odd ones still cause a seg fault).

---

