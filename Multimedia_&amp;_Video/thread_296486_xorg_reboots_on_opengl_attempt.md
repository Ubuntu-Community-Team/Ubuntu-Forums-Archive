---
title: "xorg reboots on opengl? attempt"
date: 2006-11-09
forum: Multimedia &amp; Video
---

### Post by Clunsford on 2006-11-09
Edgy x86_64, Nvidia Beta Driver 1.0-9629 from [http://albertomilone.com/drivers/edgy/nonlegacy/64bit](http://albertomilone.com/drivers/edgy/nonlegacy/64bit) binary/, when I attempt to launch the 3d FPS Tremulous or Nexuiz xorg reboots as screen attempts to go full(?), Beryl and other hardware accelerated apps seem to work flawless.

I unfortunately don't get to see any console output about the crashes, nor dos xorg.log contain anything about the crash (that im not seeing perhaps?)


Everything on system taken from ubuntu repo's minus the beryl and Nvidia beta driver. Also i don't think there is anything wrong with my xorg.conf, but i am not an xorg guru.

I am going to assume other 3d game apps will behave this way too like UT2004 and Q4. Would really like to get this problem solved soon, because if we do, I can finnaly cast out that pesky windirectex9 partition!

---

### Post by dpw2atox on 2006-11-09
From what i understand it is a bug with compiz and beryl. 

[http://lists.freedesktop.org/archives/compiz/2006-November/000738.html](http://lists.freedesktop.org/archives/compiz/2006-November/000738.html)

there is the thread about the issue with compiz.

Once this is fixed it should work fine. Remember both pieces of software are alpha/beta so there will be bugs. I have found from my own experience though that compiz is much more stable than beryl. Hope this helps.

---

### Post by skymt on 2006-11-09
Does glxgears work?

When I tried the beta drivers, OpenGL just plain broke. You may want to revert to the old stable drivers that come with Edgy, and use XGL. Another option is to try the brand-new stable 9000-series drivers from the nVidia web site.

---

### Post by Clunsford on 2006-11-09
ok... how on earth do i revert to the stable driver then?  apt wants to uninstall xorg and everything to remove the nvidia-xgl...

---

### Post by skymt on 2006-11-09
I used aptitude. Start by running "sudo aptitude" in a terminal. Find the "nvidia-glx" package (not -dev!) using search (hit "/" to search, "n" to go to the next result), and hit enter. At the bottom of the nvidia-glx page (use the up and down arrow keys to navigate) there's a section called "versions". Select the version of the stable (8000-series) drivers that goes with your kernel version, and hit "+" on your number pad. It will complain about a broken package, so hit "e" to go to the conflict resolution mode. Find a resolution (using "." to go forward, "," to go back) that doesn't involve removing anything, and hit "!" to apply it. Then hit "g" twice, to apply changes and confirm that you really want to do it.

Let me know if this works for you.

---

### Post by Clunsford on 2006-11-09
ahhhhh discoverd the stable 9000 drivers! all is well.

---

