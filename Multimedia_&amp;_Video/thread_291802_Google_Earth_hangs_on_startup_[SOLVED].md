---
title: "Google Earth hangs on startup [SOLVED]"
date: 2006-11-03
forum: Multimedia &amp; Video
---

### Post by malacandra on 2006-11-03
Saw this in a closed thread and had a similar problem:

I'm running a Dell Latittude D810 with an ATI Radeon Express 300 video card. Running the fglrx drivers for video acceleration. Google Earth worked fine before the uprgrade.

Did a distro upgrade from Dapper to the release of Edgy. Made a few tweaks to get everything working, but Google Earth kept hanging at the splash screen. I had no problems running it under Dapper.

After several tries, I did the following and now it works. Perhaps it will help others.

(1) Copy all .kmz and .kml files to a separate directory (they are located in the Google Earth directory and in your /home/name/.googleearth directory.

(2) Run the uninstall script for google-earth in the google-earth directory (or wherever you had it installed).

(3) Delete all files and the .googleearth directory (the hidden directory in your home folder).

(4) Install the latest version of Google Earth. (I installed in my home directory; no root privileges needed; I installed as myself)

(5) Reboot.

That seems to have done it for me. I hope it works for others!

---

### Post by gala on 2006-11-03
Then what about copied files?

---

### Post by malacandra on 2006-11-03
> **gala said:**
> Then what about copied files?

Put them back in the directories you copied them from. The directories will be put back when you install again.

---

### Post by malacandra on 2006-11-03
Update: Looks like we're back to hanging. When I hibernate the laptop and then restore, Google Earth now hangs as usual. A reboot lets you run it again, but that's not entirely convenient.

I'm anxious to see if any better or more complete fixes are found. :confused:

---

### Post by gala on 2006-11-04
Dear malacandra, thank you for replay, I applied your instructions, but no success. Waiting for solution.

---

### Post by Samir33 on 2006-11-07
Happends on my Edgy amd64 too. Freezes on splash screen. I tried newest GooglEearth version, same problem. I think it's related to ati fglrx drivers. Are you people using fglrx?

---

### Post by chadd on 2006-11-07
Yes, same problem here, and I am using the fglrx drivers.  Anybody know the fix?

---

### Post by gala on 2006-11-07
I am using the fglrx drivers too.

---

### Post by tuberculo on 2006-11-07
I've tried [this]("http://bbs.keyhole.com/ubb/showthreaded.php/Cat/0/Number/674910/an/0/page/0#674910"), but I had no success.
Backup your xorg.conf. Had to revert changes to make system functional.

---

### Post by Samir33 on 2006-11-08
> **tuberculo said:**
> I've tried [this]("http://bbs.keyhole.com/ubb/showthreaded.php/Cat/0/Number/674910/an/0/page/0#674910"), but I had no success.
Backup your xorg.conf. Had to revert changes to make system functional.
I had to do that step to enable fglrx's OpenGL 3D accel. Without it my ATI Mobility worked only in software (Mesa) OpenGL mode... There must be some other thing, but what?!? Have you seen [this]("http://ubuntuforums.org/showthread.php?t=196011") thread about same issue?!?

---

### Post by maxwellcom on 2007-02-27
same problem here, anyone find a solution?

---

### Post by scott_evil on 2007-03-01
Yes, it can be fixed by using an older version of libGL.so

[see here]("http://bbs.keyhole.com/ubb/showflat.php/Cat/0/Number/696534/Main/620003/")

---

