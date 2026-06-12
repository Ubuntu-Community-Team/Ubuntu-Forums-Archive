---
title: "XGL Crashes with ATI 8.28.8"
date: 2006-08-22
forum: Multimedia &amp; Video
---

### Post by Greycloak on 2006-08-22
Ever since I installed Ubuntu a few weeks ago I have been trying to get XGL/Compiz to work.  After many failed attempts I decided to reinstall Ubuntu and start from scratch with the new 8.28.8 drivers from ATI.

My problem is that everytime I try to login to an Xgl session, the desktop completely freezes.  With previous driver versions I could login to the Xgl session but everything ran extremely slow.  With this driver I can see Xgl starting (the checkerboard pattern), but my system freezes and I have to reboot.

I have a Radeon 9200 PCI, and direct rendering works perfectly in a normal gnome session. Any help with this would be greatly appreciated.  It's frustrating to know that people have gotten this to work with a Radeon 8500 and I STILL can't figure it out.

---

### Post by Nordkraft on 2006-08-22
I'm running this flawlessly on my box - my gfx is an X1900XTX. Basically, all I did was follow this tutorial for installing the driver: 
[http://www.ubuntuforums.org/showthread.php?t=204910](http://www.ubuntuforums.org/showthread.php?t=204910)
and this for installing XGL and Compiz:
[http://www.compiz.net/viewtopic.php?id=389](http://www.compiz.net/viewtopic.php?id=389)

Don't know if this is how you did it too, but it sure works for me:)

---

### Post by Greycloak on 2006-08-22
I had no problems installing the 8.28.8 drivers. I've looked through almost all of the howto's on XGL/Compiz but nothing seems to work.  The system crashes on Xgl startup.  I don't even get the opportunity to start compiz/cgwd.

With the older drivers XGL would start, but everything ran sluggish.  With the new drivers XGL seems to start alright, but as soon as my desktop finishes initializing everything freezes and I need to reboot to the normal gnome session. I can still move the mouse pointer though.

---

### Post by TheTerl on 2006-08-24
I've been having, for all practical purposes, the exact same problem.  I've installed Xgl and compiz based on the different guides floating around here.  I can start a session using Xgl, and the compiz plugins work, but after some amount of time (it's taken less than a minute or as long as ten) the desktop 'crashes' in the sense that it becomes completely unresponsive, "freezing" like the previous post describes--I can move the cursor, but mouse clicks and keyboard keys do nothing, and the only option at that point is a hard reboot.  These crashes are consistent, but I haven't been able to link them to any specific application or effect.  This only happens in Xgl sessions, GNOME loads and works just fine.

I run a Radeon 9600XT with the fglrx drivers ( v 8.25.18 ) installed, and I've used Update Manager to make sure I have the latest released packages.

Does anyone have some suggestions?  Aside from this post, I haven't found anyone else who was having a similar problem.  I'd hate to chalk this up to general instability in Xgl/compiz when I hear about everyone else running it just fine.  Thanks a lot.

---

### Post by Servus on 2006-08-25
video card ati 9200

I have just installed the newest drivers: 8.28.8. When I start the xgl session no windows borders appears. A few weeks ago I tried to install xgl and compiz with different drivers. Results: compiz did not work well because started randomly 1 time each 10 startcompiz command!
Now nothing happens. Could it be a matter of drivers? Could somebody with ati 9200 suggest me the correct drivers version?
thx.
servus!

---

### Post by Greycloak on 2006-08-25
I have noticed something new.  When I try to start an Xgl session, I get a message that 'Your session has lasted less than 10 seconds..."  or something to that effect.  I get immediately returned to the login screen.

---

### Post by bigbamboo on 2006-09-02
Hi everybody,
did you manage to find a solution for this problem?
I run a Radeon X800 with the fglrx drivers ( v 8.28.8 ) installed and the XGL session freezes in the same way.

thanks for any advice.
BB

---

