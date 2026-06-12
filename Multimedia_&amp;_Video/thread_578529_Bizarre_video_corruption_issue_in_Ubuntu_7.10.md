---
title: "Bizarre video corruption issue in Ubuntu 7.10"
date: 2007-10-17
forum: Multimedia &amp; Video
---

### Post by ravalox on 2007-10-17
I have a completely currently patched version of Gutsy Gibbon installed.  It's got mythtv installed.  I have an Nvidia 7800 GS and the nvidia-glx-new driver package running it.  Everything was running fine... until I installed stellarium.  Now here's what's so strange; when I run Stellarium it work fine.  But after exiting stellarium NONE of my video playback works!  If I run VLC, xine, or mplayer I get a messy garble of green instead of video!  The same is true of mythtv.  So I reboot and everything works fine.  Then this morning I woke up to find it had the same issue; without running stellarium?  What could possibly cause all video playback to not work?

---

### Post by nesl247 on 2007-10-17
Same issue, and it's not just ubuntu. It has to do with the newest nvidia and xv I think, because if you don't use xv, you won't have the issue.

---

### Post by oedipuss on 2007-10-24
Same here, only it happened without any particular cause that I can identify. Sometimes the xv video just gets corrupted. 
It appears to fix itself after restarting the xserver (quicker than a full reboot), but its still rather annoying.

Any idea if it's fixed in the 100.14.23 beta driver?

---

### Post by lvleph on 2007-12-03
I don't have nvidia and I have the same problem, but have never installed stellarium.

[another thread discussing the problem](http://ubuntuforums.org/search.php?searchid=32397811)

---

### Post by treris on 2007-12-07
Same problem, every once in a while I'll just see a green screen while the sound in movies etc. is still working fine. Up till now a reboot or x-server restart has done the trick fixing it, but I would just like to fix it more permanently. Does anybody have any clues?

---

### Post by meganox on 2007-12-09
mine is pink.  happens after playing a corrupt video in vlc, mplayer or totem.  appears to be xv related, would love to find a way to reset it without having to log out.

---

### Post by Bofirial on 2007-12-09
[[IMG]http://img255.imageshack.us/img255/1820/screenshotys2.th.png[/IMG]](http://img255.imageshack.us/img255/1820/screenshotys2.png)   [[IMG]http://img235.imageshack.us/img235/5766/screenshot1iy6.th.png[/IMG]](http://img235.imageshack.us/img235/5766/screenshot1iy6.png)

This the corruption you guys are getting?  The green is usually accompanied with a system crash shortly after (screen freezes and I can't do anything but move the mouse). The pink is easily fixed with a 

I find it odd that video thumbnails still work in MythTV: [[IMG]http://img411.imageshack.us/img411/5932/screenshot2wf7.th.png[/IMG]](http://img411.imageshack.us/img411/5932/screenshot2wf7.png)
but the moment you try and watch the video w/ sound: [[IMG]http://img89.imageshack.us/img89/336/screenshot3ve2.th.png[/IMG]](http://img89.imageshack.us/img89/336/screenshot3ve2.png)

So does this happen with all NVidia cards or could buying a new one possibly help matters?

---

### Post by crjackson on 2007-12-14
> **Bofirial said:**
> [[IMG]http://img255.imageshack.us/img255/1820/screenshotys2.th.png[/IMG]](http://img255.imageshack.us/img255/1820/screenshotys2.png)   [[IMG]http://img235.imageshack.us/img235/5766/screenshot1iy6.th.png[/IMG]](http://img235.imageshack.us/img235/5766/screenshot1iy6.png)

This the corruption you guys are getting?  The green is usually accompanied with a system crash shortly after (screen freezes and I can't do anything but move the mouse). The pink is easily fixed with a 

I find it odd that video thumbnails still work in MythTV: [[IMG]http://img411.imageshack.us/img411/5932/screenshot2wf7.th.png[/IMG]](http://img411.imageshack.us/img411/5932/screenshot2wf7.png)
but the moment you try and watch the video w/ sound: [[IMG]http://img89.imageshack.us/img89/336/screenshot3ve2.th.png[/IMG]](http://img89.imageshack.us/img89/336/screenshot3ve2.png)

So does this happen with all NVidia cards or could buying a new one possibly help matters?

I have the exact same issue.  Here's my thread [http://ubuntuforums.org/showthread.php?t=640675]("http://ubuntuforums.org/showthread.php?t=640675")

If you find a solution, please post it here.

---

### Post by crjackson on 2007-12-15
Okay, I have found that I can get it working with CTRL+ALT+BACKSPACE. If I turn OFF desktop effects, the problem is back. I then C+A+B and it fixes it now. If I turn ON desktop effects the problem comes back again, and CAB fixes this too.

Since I've been playing with desktop effects a lot, I guess this has been my problem. Now, I just wonder how long it will work correctly if I make NO more changes. If it continues to work properly, I guess the fix is to ALWAY C+A+B after making changes related to desktop effects. I could live with that. Only time will tell...

---

### Post by dannystaple on 2007-12-26
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/162343](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/162343) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				CTRL-ALT and backspace is actually killing the X-server. However, your observation on desktop effects (a big change in Gutsy apart from those living on the edge before) may be the key. I will try to turn these off and see how it effects this issue.

There is also now a related defect report.

---

### Post by angelwolf on 2008-02-17
I got the same thing with the video corruption. What i want to ask, is it normal that this happens just in my ubuntu installation? I added xfce as a window manager, and i have never noticed this corruption during my xfce session,,and is it me or does ubuntu get a bit buggy! i made a clean install when it came out, worked perfectly (hadnt noticed the video corruption at all, this started sth like a month ago), and now applications crash etc. etc. Anyway,,,

---

