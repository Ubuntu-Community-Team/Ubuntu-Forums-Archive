---
title: "ATI XPRESS 200M is going to make me freak out"
date: 2006-11-15
forum: Multimedia &amp; Video
---

### Post by casperiv on 2006-11-15
I have tried every how-to I can find on these forums, but none seem to work.  Here is where I'm at.  I have downloaded ati-driver-installer-8.29.6.run and made the deb files.  I installed them.  I rebooted. I ran fglrxinfo and got this:

> \Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)


I read through some more threads and found random fixes... none of which worked.  I tried to run the deb for the driver again and it said it "Error: Conflicts with the installed package 'xorg-driver-fglrx'" which when I look it up in Synaptic, is the correct version number.

So, from what I can tell, I have the newest drivers which ATI says will work with my 200M, have followed and checked many threads about this 200M, but can't get it to actually work... or at least the 3D to work.  It works fine for the desktop and 2D stuff like running Diablo II without opengl.

Please help point me in the right direction before I explode.

---

### Post by playboy601 on 2006-11-15
I've been frustrated with this as well, but it seems like 200m dri support was broken after all releases after 8.24. I've tried reverting back to those drivers, but I can't get them to build with the newer version of xorg installed. You can submit a support request to the ATI linux crew by clicking on the link below.. sure hope they fix this in the next release.. 

[http://support.ati.com/ics/survey/survey.asp?deptID=894&surveyID=508&type=web]("http://support.ati.com/ics/survey/survey.asp?deptID=894&surveyID=508&type=web")

---

### Post by dutchmega on 2006-11-15
> **casperiv said:**
> I have tried every how-to I can find on these forums, but none seem to work.  Here is where I'm at.  I have downloaded ati-driver-installer-8.29.6.run and made the deb files.  I installed them.  I rebooted. I ran fglrxinfo and got this:



I read through some more threads and found random fixes... none of which worked.  I tried to run the deb for the driver again and it said it "Error: Conflicts with the installed package 'xorg-driver-fglrx'" which when I look it up in Synaptic, is the correct version number.

So, from what I can tell, I have the newest drivers which ATI says will work with my 200M, have followed and checked many threads about this 200M, but can't get it to actually work... or at least the 3D to work.  It works fine for the desktop and 2D stuff like running Diablo II without opengl.

Please help point me in the right direction before I explode.

(Re)Install the following: xserver-xorg-video-all, libgl1-mesa-dri and libgl1-mesa-glx. After that install the fglrx-driver again.
Make sure that dri and glx are loaded in your xorg.conf

---

### Post by casperiv on 2006-11-15
I'll try it.  I checked my xorg.conf and both were loaded, so I'll remove everything and redu those 3 and see if it helps.

---

### Post by casperiv on 2006-11-15
Well, I tried that, and I tried going back to 8.26.18... nothing worked.  Right now I'm using 8.29.6 and X loads, but I get no 3D.  I am still getting the same result when I run fglrxinfo.  When I ran 8.26 built it wouldn't let me build Ubuntu/edgy, so I retried building Ubuntu/Dapper and it built, but won't load with it.

Someone please give a direction to go from here.

---

### Post by casperiv on 2006-11-16
Ok, I have tried reinstalling the packages suggested by dutchmega, and reinstalling 8.29, then I tried removing the xorg-driver packs and starting over, no good.  No matter what I do, when I do fglrxinfo after reboot I always get:
>  \Xlib: extension "XFree86-DRI" missing on display ":0.0".
display: :0.0 screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)
And when I attempt to load anything with opengl it says that the 3d fails to start.  I checked my xorg.conf agan and the dri and glx are both selected.  Please, someone give me an idea here.  When I get home I'll post my last attempt line by line and see where I'm going wrong.

---

### Post by mrunion on 2006-11-17
The 200M needs 8.24 or less.  You can't use 8.26 or 8.29.  Read the ATI how-to, but install 8.24.xx and it'll work.  I have the same card.  Search for my poosts and you'll see how I got it to work.  It's the 8.24 thing.  That's as high as you can go and get 3D accelleration.

Thanx,
Matt

---

### Post by casperiv on 2006-11-17
I'm still trying to find where I can download that old driver.  When I find it I'll give it a shot.

---

### Post by oskie on 2006-11-17
I have this dreaded card as well but I did have 3D enabled under Dapper (with that old driver I think) but I can no longer find it. Will the old driver work with the latest kernel?

---

### Post by casperiv on 2006-11-17
Good luck, I just downloaded 8.24.8 and am having a heck of a time getting it to build as edgy.  I am going to try to build it as Dapper, but I'm pretty sure this will make it error when X loads.  We will find out soon.

---

### Post by casperiv on 2006-11-17
Yeah, I have been trying to use the following methods:
> sudo ./ati-driver-installer-8.24.8-x86.run --buildpkg Ubuntu/edgy
Won't let me build this package. So...
> sudo ./ati-driver-installer-8.24.8-x86.run --buildpkg Ubuntu/dapper
Get's a lot farther with this, but fails out after it starts trying to make the deb packs.

I am starting to really get annoyed with these ATI drivers.

---

### Post by oskie on 2006-11-17
> I am starting to really get annoyed with these ATI drivers.

Tell me about it. Hopefully AMD's purchase of ATI will result in open source drivers soon. If not, my next computer will use Intel video cards.

---

### Post by casperiv on 2006-11-18
Well ATI cards are great as far as hardware.... I just wish the drivers would actually let us use the hardware.  I have always had highend Nvidia and ATI cards, and the drivers for ATI cards have always been a problem.  Let's hope the Fusion series from AMD doesn't suffer from anything like this :)

---

### Post by playboy601 on 2006-11-20
the 8.24 drivers won't build because the version of xorg installed on edgy is 7.11, the ati drivers are looking for 7.10. The installer is binary so I can't hack it to not do that check. So, in order to get 3d acceleration, you'll have to revert back to xorg 7.10 or less, then revert back to the 8.24  or less drivers. Of course, the newer kernel might also have a negative effect causing the older ati drivers not to build. Basically, it's up to ATI to release some working drivers for the 200M Xpress chipset, and there's probably nothing that we, as end users, can do. ](*,)

---

