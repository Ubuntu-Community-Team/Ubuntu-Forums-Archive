---
title: "DVD Video Glitching"
date: 2008-12-28
forum: Multimedia Software
---

### Post by Matthiacon on 2008-12-28
I'm new to Ubuntu 8.10, and am having difficulty with the Totem movie player.  While the DVD is playing, the video spontaneously (and constantly) glitches in and out of a black screen (in a window & full-screen mode).  I have performed the following installation procedures:

1.[https://help.ubuntu.com/8.10/musicvideophotos/C/video.html](https://help.ubuntu.com/8.10/musicvideophotos/C/video.html)
2.[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
3.[http://ubuntuforums.org/showthread.php?t=1020760&highlight=playing+dvds](http://ubuntuforums.org/showthread.php?t=1020760&highlight=playing+dvds)

My hardware:

AMD Athlon64 3400
ATI x1600 pro (AGP)
Plextor 708A
Pioneer DVD-115
MSI motherboard w/onboard sound (RealTek ALC655 chip)

It appears to be a video issue.  The DVD glitches in either DVD drive, but the sound works great!  I originally had a M-audio 2496 sound card installed, but it wouldn't work with ALSA or OSS out-of-box.  But I'm more concerned with fixing this video problem right now.  Please help!

I will try reading the Comprehensive Multimedia & Video How-to.

---

### Post by Matthiacon on 2008-12-28
I went to the 'Appearance Preferences' and select 'None'.  It fixed the problem, but now I have no aesthetically pleasing desktop effects.  Any ideas of how to reconcile my dilemma?

---

### Post by Sin@Sin-Sacrifice on 2008-12-28
What video drivers you have installed?

---

### Post by Matthiacon on 2008-12-28
I'm using the proprietary 'ATI/AMD FGLRX' graphics driver.  I tried deactivating it and running the default installation open-source drivers.  The behavior is the same (no glitching in 'None' appearance setting, but glitching in 'normal' and 'extra' setting.

---

### Post by lavinog on 2008-12-29
This is a known issue.
It is supposed to be fixed with DRI2
One way to get non flicker video with compiz is to not use accelerated video.
set your video out to X11 instead of Xv

---

### Post by Matthiacon on 2008-12-29
I'm brand new to Linux (switching over from Windows), but am computer literate.  I must admit, I do not fully understand what DRI2 is or the X Window System.  So let me try to expose my understanding (or lack thereof)!

From my understanding, DRI2 is an extension that works with Window Managers such as Compiz, Beryl, etc. that use the X Window System (please bear with me, I'm winging this).  Moreover, I'm guessing 'Xvideo' is an extension that when set to 'Xv' uses the video card's on-board 3d acceleration to produce video, thus taking the load off the CPU.  So if I switch to 'X11', won't that decrease my performance considerably?  Lastly, I do not no how to adjust the “video output setting.”

I'm not sure how each Window Manager composts its windows:  Perhaps they render each individually?  Or does it port each window to a singular GUI interface?  By the way, what is the 'Mesa Package' and 'xFree86' (any good links will suffice)?

In any case, I'm willing to change my Window Manger from Compiz to something else fancier like Beryl if it means I can have good desktop effects+no video flickering.  Last question:  Is DRI2 enabled/supported by default in Ubuntu 8.10 (amd64)?  If not can I download it using the package manager or apt-get?

---

### Post by lavinog on 2009-01-01
> **Matthiacon said:**
> I'm brand new to Linux (switching over from Windows), but am computer literate.  I must admit, I do not fully understand what DRI2 is or the X Window System.  So let me try to expose my understanding (or lack thereof)!
Welcome. There can be some hurdles with Linux, but there can be many rewards. I have switched from windows over 2 years ago. I am always learning something new, but I feel like I have so much more control over my computer now. I have a couple computers that can dual boot, and I only seem to boot to windows once every two months. The rest of my computers run only linux. I even use Ubuntu at my office.

> 
From my understanding, DRI2 is an extension that works with Window Managers such as Compiz, Beryl, etc. that use the X Window System (please bear with me, I'm winging this).  Moreover, I'm guessing 'Xvideo' is an extension that when set to 'Xv' uses the video card's on-board 3d acceleration to produce video, thus taking the load off the CPU.  So if I switch to 'X11', won't that decrease my performance considerably?  Lastly, I do not no how to adjust the “video output setting.”
From what i understand, The X window system was designed as a client server model. It offers alot of flexibility in the way it can be used, but has a performance hit with graphics. The DRI allows programs to directly access the video hardware, thus improving performance on a desktop.
DRI2 is the new specification. One of the issues it addresses is the flickering of video/opengl apps with compositing window managers.

> 
I'm not sure how each Window Manager composts its windows:  Perhaps they render each individually?  Or does it port each window to a singular GUI interface?  By the way, what is the 'Mesa Package' and 'xFree86' (any good links will suffice)?

Mesa drivers are kind of like universal drivers...if no other video driver works with your card, the mesa drivers should always work. They usually have reduced or no acceleration though.
xFree86 is a windowing system, like X11. I don't know what the actual differences are. I think the difference is the licensing.
wikipedia has alot of good info on linux related stuff

> 
In any case, I'm willing to change my Window Manger from Compiz to something else fancier like Beryl if it means I can have good desktop effects+no video flickering.  Last question:  Is DRI2 enabled/supported by default in Ubuntu 8.10 (amd64)?  If not can I download it using the package manager or apt-get?
Compiz and Beryl merged. Switching to a nVidia card has been known to fix the issue, because nVidias drivers have a hack in them to address the issue. ATI was anticipating DRI2 to fix the issue and held off on making hacks. This could have been a good move on ATI's part, but the DRI2 specs were changed recently (I think by Intel.) This change delayed DRI2 being implemented in Ubuntu 8.10, but should be ready for 9.04

---

### Post by lavinog on 2009-01-01
> **Matthiacon said:**
> CPU.  So if I switch to 'X11', won't that decrease my performance considerably?  Lastly, I do not no how to adjust the “video output setting.”


Sorry got distracted and forgot to answer this question.
Yes, you will get a performance hit.
It might be better to disable desktop effects if you are planning to watch a video.
Apparently the multimedia systems selector is hidden by default now...I don't know why.
goto to System>Preferences>Main Menu
You should look around, you might find a couple of menu items turned off.
if you look under System>Preferences, you should see multimedia systems selector unchecked...check it.
Now you should have it in your menu.

---

### Post by Matthiacon on 2009-01-01
Thank you for the help!  BTW...how do I "thank" someone for helping me (the post counter in the left column)?

---

### Post by lavinog on 2009-01-02
The little medal thing on the bottom right side of each post.
[img]http://ubuntuforums.org/images/buttons/post_thanks.gif[/img]<--looks like this

---

