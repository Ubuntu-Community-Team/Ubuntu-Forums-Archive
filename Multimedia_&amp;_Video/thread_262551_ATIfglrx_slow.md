---
title: "ATI/fglrx slow"
date: 2006-09-21
forum: Multimedia &amp; Video
---

### Post by kook44 on 2006-09-21
Hi-
I have an ATI Radeon X300 PCIE card running gnome/dapper.
I'm using the fglrx driver (i installed it with synaptic and then changed the Driver setting in xorg.conf to "fglrx").
The screen looks nice, i got full resoultion @ 1920x1200, but it's kind of slow.  I don't play any games or anything, but drop-down menus, moving windows, and switching between them is slow.  When I go to shutdown and the desktop "dims", it's noticeably slow.
This is frustrating - I assume it's pretty good hardware. Is there anything I can do to speed it up?

I'm not even sure what fglrx is.  Is it just an open source driver that is semi-compatible with ATI?  Is there any way I can tweak it to run at full capacity?
I also see there are ways to use the real ATI drivers.  May look into that...

---

### Post by Ferrat on 2006-09-21
Try installing the newest ATi Driver

---

### Post by bittergourd on 2006-09-22
try type in "glxinfo" or "fglrxinfo", see what it tells you. if it displays "mesa" something instead of fglrx, that means the driver is not used at all. you can also try "glxgears" to see how fast it works.

the other thing you can try is check /var/log/Xorg.0.log, and /var/log/gdm/:0.1og, see where the problem exactly is.

what motherboard are you using?

---

### Post by WalmartSniperLX on 2006-09-22
Ati's crappy linux (fglrx) drivers are garbage, making ati (if you use linux) garbage. I use ati (x1600pro) and i just got the newest driver 30 min ago. No improvements. Ati releases drivers every month because they made a promise to, not because they're fixing problems. If you look at the release notes, under known problems, it seems that for the last 5 releases or so, you'll notice that they didnt fix a damn thing. 

and yes im experiencing slowness too, but thats just ati (with linux) for now :D

---

### Post by bittergourd on 2006-09-22
i think for 8.29.6, it just kicks out some old card from the support list. nothing else.

now they are amd/ati. what do you expect from a homeless?

---

### Post by Ferrat on 2006-09-22
> **WalmartSniperLX said:**
> Ati's crappy linux (fglrx) drivers are garbage, making ati (if you use linux) garbage. I use ati (x1600pro) and i just got the newest driver 30 min ago. No improvements. Ati releases drivers every month because they made a promise to, not because they're fixing problems. If you look at the release notes, under known problems, it seems that for the last 5 releases or so, you'll notice that they didnt fix a damn thing. 

and yes im experiencing slowness too, but thats just ati (with linux) for now :D

The new driver was just small fixes and discontinuing of some cards, Im running my x800XT PE at more or less same FPS as in windows playing WoW and CSS, doom3 pushes out 5-10 more FPS in linux. 

but I agree with you that they should put a bi more effort in it and fix at least the major problems that ATi has in linux

---

### Post by tseliot on 2006-09-22
you can try the latest ATI driver from my testing repositories:
[http://ubuntuforums.org/showthread.php?t=255929](http://ubuntuforums.org/showthread.php?t=255929)

---

### Post by IDeus on 2006-09-22
How are you getting something different than mesa when installing the ATI drivers? I uninstalled everything having to do with fglrx until fglrxinfo returned nothing. This even uninstallled my KDE. Then I installed the ati drivers with the sh atidrivername....run and it shows Mesa again???

---

### Post by WalmartSniperLX on 2006-09-22
> **Ferrat said:**
> The new driver was just small fixes and discontinuing of some cards, Im running my x800XT PE at more or less same FPS as in windows playing WoW and CSS, doom3 pushes out 5-10 more FPS in linux. 

but I agree with you that they should put a bi more effort in it and fix at least the major problems that ATi has in linux

May I ask you what method you used to install your driver :D

---

### Post by kook44 on 2006-09-22
> **bittergourd said:**
> try type in "glxinfo" or "fglrxinfo", see what it tells you. if it displays "mesa" something instead of fglrx, that means the driver is not used at all. you can also try "glxgears" to see how fast it works.

the other thing you can try is check /var/log/Xorg.0.log, and /var/log/gdm/:0.1og, see where the problem exactly is.

what motherboard are you using?

i will try this tonight.
I think I remember changing the driver from what it was previously - something called "vesa"?? (could that be right?)

---

