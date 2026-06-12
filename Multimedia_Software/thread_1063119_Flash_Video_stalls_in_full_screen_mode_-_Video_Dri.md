---
title: "Flash Video stalls in full screen mode - Video Driver?"
date: 2009-02-07
forum: Multimedia Software
---

### Post by crjackson on 2009-02-07
I've got a new HP dv6929nr laptop.  It has an Intel core2 Duo at 2.0 GHz and and Intel x3100 Graphics Media Accelerator Video card.

Here's the problem. While watching online movies or video clips in full screen flash, the video pauses, stops, and jerks. In a window it plays fine.

The same video running under Vista is fine as well. Flash 10 is being used in each case.

Is this due to the poor video driver in linux, or is there another consideration.

No other tasks are being performed while the video is running.

Thanks

---

### Post by overdrank on 2009-02-07
Hi and it may be the driver as I have seen several threads involving the intel graphics and Intrepid. How much memory is shared with the integrated graphics as this may help some if you can increase.
Moved to Multimedia & Video :)

---

### Post by crjackson on 2009-02-07
> **overdrank said:**
> Hi and it may be the driver as I have seen several threads involving the intel graphics and Intrepid. How much memory is shared with the integrated graphics as this may help some if you can increase.
Moved to Multimedia & Video :)

Well, intrepid was awful on this system due to slow desktop response, so I installed Hardy which is noticeably better.

Regarding shared memory I don't have a clue. I didn't think of that since it was running smooth in Vista. I'll check the bios and see if there is a setting. What would you suggest for this setting. The laptop has 4GB installed memory.

---

### Post by overdrank on 2009-02-07
Well for me it is always turned up to the max :)
Sorry for the assumption that you were using intrepid.

---

### Post by crjackson on 2009-02-07
> **overdrank said:**
> Well for me it is always turned up to the max :)
Sorry for the assumption that you were using intrepid.

There doesn't seem to be any settings in bios for anything video or memory related. Could there be some hidden settings somewhere?

---

### Post by crjackson on 2009-02-08
bump

---

### Post by crjackson on 2009-02-09
bump

---

### Post by redroad55 on 2009-02-09
This may be a long shot but check this out ..[http://ubuntuforums.org/showthread.php?t=1034369&highlight=full+screen]("http://ubuntuforums.org/showthread.php?t=1034369&highlight=full+screen")
post back

---

### Post by crjackson on 2009-02-09
> **redroad55 said:**
> This may be a long shot but check this out ..[http://ubuntuforums.org/showthread.php?t=1034369&highlight=full+screen]("http://ubuntuforums.org/showthread.php?t=1034369&highlight=full+screen")
post back

Thanks, yeah it's a bit too long of a shot. Everything on my system is perfectly supported that I can tell. My only complaint is the poor flash play back at FS.

Thanks for the reply and effort...

---

### Post by redroad55 on 2009-02-09
I see you have been struggling with this a few days now .. When I put "full screen " in the search engine I get this has been an issue for awhile .. There has to be some kind of common denominator. I really don't think it's flash or if it is it is some sort of config issue .. what are your thoughts about it ..Post back

---

### Post by crjackson on 2009-02-09
> **redroad55 said:**
> I see you have been struggling with this a few days now .. When I put "full screen " in the search engine I get this has been an issue for awhile .. There has to be some kind of common denominator. I really don't think it's flash or if it is it is some sort of config issue .. what are your thoughts about it ..Post back

I don't know. I don't feel it's flash. if that were the case, wouldn't the problem rear it's head in windows too? It doesn't.

I'm thinking it's the intel video driver for linux. I was hoping someone might know a tweak or alternate driver fix.

I don't even know how to tell which verson of the intel version is installed.

---

### Post by holdthewine on 2009-02-09
I have this same exact problem with the same on-board video, too. Also, if I'm watching it in window mode, sometimes I can hear the sound but no video is played (just a white box). If I hit refresh a few times it usually works correctly. Anybody have any ideas?

---

### Post by redroad55 on 2009-02-09
Humor me on this try logging in a new account ..post back

---

### Post by crjackson on 2009-04-01
> **redroad55 said:**
> Humor me on this try logging in a new account ..post back

What I had to do was replace Intrepid with Hardy.

BTW, I'm not having this problem with Juanty A6 - Haven't tried the BETA on this machine as of yet. I'll try to do that this weekend.

---

### Post by Orange Kingdom on 2009-04-02
In Kubuntu (Konqueror) fullscreen works as fast as in winxp.
So it has to do something with ubuntu.

---

### Post by crjackson on 2009-04-02
> **Orange Kingdom said:**
> In Kubuntu (Konqueror) fullscreen works as fast as in winxp.
So it has to do something with ubuntu.

What version of of Kubuntu are you using?

---

### Post by Orange Kingdom on 2009-04-03
> **crjackson said:**
> What version of of Kubuntu are you using?

Kubuntu 8.10 

When i play an embedded flash video in konqueror under ubuntu (gnome) it is sloppy. Under KDE it works fast.
Perhaps a compiz problem or setting?

I just tested this with ubuntu with "visual effects"  disabled and it works as fast as in kde and winxp.

---

### Post by crjackson on 2009-04-03
> **Orange Kingdom said:**
> Kubuntu 8.10 

When i play an embedded flash video in konqueror under ubuntu (gnome) it is sloppy. Under KDE it works fast.
Perhaps a compiz problem or setting?

I just tested this with ubuntu with "visual effects"  disabled and it works as fast as in kde and winxp.

I always run without "visual effects" so that's not the issue. However Jaunty seems to have solved the problem.

---

