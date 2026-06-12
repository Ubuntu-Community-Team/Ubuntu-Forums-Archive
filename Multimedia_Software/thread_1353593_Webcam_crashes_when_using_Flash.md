---
title: "Webcam crashes when using Flash"
date: 2009-12-12
forum: Multimedia Software
---

### Post by DPic on 2009-12-12
My webcam seems to work fine other than using it with flash. After allowing a website to access my webcam through flash, it works for a second, but there's no sound. Then the image freezes, and the webcam doesn't work until i reboot my machine. Any ideas on what's causing this?

---

### Post by gordintoronto on 2009-12-13
I have run into difficulty with a webcam on a system with a slow CPU.  For example, Skype works just fine with sound and video on new computer, but it dies on my old, slow one.

---

### Post by DPic on 2009-12-13
Well...i have a quad core. I don't think that has anything to do with my problem which is specific to using my webcam with Flash.

---

### Post by jmate24 on 2009-12-13
have you tried cheese to take your picture? it is in the ubuntu software center?

jmate24

---

### Post by DPic on 2009-12-13
> **jmate24 said:**
> have you tried cheese to take your picture? it is in the ubuntu software center?

jmate24

As i said in my first post...

> **DPic said:**
> My webcam seems to work fine other than using it with flash.

So yes, i have and it works fine. But when using it with Flash, it crashes. That is the problem i'm having...as per the title of this thread

---

### Post by Fr33d0m on 2009-12-22
You actually get it to work for a few seconds?  I get the settings dialog and it locks up at that point.  Works fine in Cheese and Emesene.  It's been this way since Intrepid.  I've tried removing the profile and a clean install to no effect.

---

### Post by DPic on 2009-12-24
I'm not sure if i would actually consider it "working" but i do see my video come through for a second or two before it gets stuck on a frame

---

### Post by Fr33d0m on 2009-12-25
Well if you've looked at or tried anything in particular that got you that far, I'd like to know what.

---

### Post by DPic on 2009-12-25
> **Fr33d0m said:**
> Well if you've looked at or tried anything in particular that got you that far, I'd like to know what.

I'm using the latest 64-bit flash 10 alpha. I think this issue has been the same for all 64-bit alphas (there have been three) and the 32-bit version (but i can't remember for certain)

---

### Post by Fr33d0m on 2009-12-27
Same here, in fact I just updated it.  But I was having the problems when I was running Intrepid and Jaunty 32-bit.  Karmic was a fresh install and I still have the issue.  I was hoping there was some configuration file somewhere that you've been playing with or something like that.

---

### Post by DPic on 2009-12-28
Actually, i just tried it again and i described the problem slightly incorrectly. The camera works with flash fine up until i hit the record button.

---

### Post by Fr33d0m on 2010-01-06
Well I'm on board with you to some extent as well.  Mine almost certainly is not a web cam problem.  If I adjust the configuration to allow without asking, the camera works.  It seems a bit rough and has to some extent been intermittent, but it works.  So now I'm even more perplexed.

---

### Post by DPic on 2010-01-11
Mine is set to work without asking as well but as soon as i hit that record button the image freezes

---

### Post by no2498 on 2010-01-11
you most likely did this by now
try cleaning out the cache and temp files

---

### Post by DPic on 2010-01-12
> **no2498 said:**
> you most likely did this by now
try cleaning out the cache and temp files

Yeah this is a problem on multiple browsers (Epiphany, Chromium, and Firefox) and happened on jaunty as well as karmic and probably intrepid as well. I'm also pretty sure it's the same for 32 as well as 64 bit

---

### Post by no2498 on 2010-01-14
what program you trying  to use to record with

---

### Post by DPic on 2010-01-14
> **no2498 said:**
> what program you trying  to use to record with

Flash. Sites like YouTube, Facebook, and others use Flash for record video directly from webcam

---

### Post by Fr33d0m on 2010-01-24
Not to be strident but it is as the subject says--Flash.

Mine had the problem on 32-bit Jaunty and after a fresh install of 64-bit Karmic.  I reformatted to ext4 so there is no chance that some cache or other file persisted.  I also had several reinstalls with reformatting to clear other problems.

I tried removing the profile several times between Hardy and Jaunty.

---

### Post by DPic on 2010-03-16
Apparently this is a problem with flash, and it can be worked around. The only program i have heard of that does this is Webcam Studio: 
[http://sourceforge.net/projects/webcamstudio/](http://sourceforge.net/projects/webcamstudio/)

Unfortunately, it does not work for me-- and i do not need all of the features it has. Hopefully this may help people

And maybe it will give helpers and idea of what i need to be able to use my webcam with most flash websites. Is there some other application that i can use, or can someone help me figure out why webcam studio won't do the trick for me?

**Edit**: for details-- previously (without webcam studio) flash detected my webcam, but crashed. Crashed may not be the best word. Flash was still responsive, but my webcam would freeze and be inaccessible until i quit out of the browser. Now, (with webcam studio), my webcam isn't even detected, although the microphone seems to be (though i'm not positive it's the webcam's microphone, or if it works)

**Edit**: I found more! Flashcam looks like it could help [http://www.swift-tools.net/Flashcam/](http://www.swift-tools.net/Flashcam/) but i can't get it to install and there are no debs anywhere. I have filed packaging requests for webcamstudio and flashcam-- [https://bugs.launchpad.net/bugs/539963](https://bugs.launchpad.net/bugs/539963) [https://bugs.launchpad.net/bugs/539965](https://bugs.launchpad.net/bugs/539965)

**Edit**: Even more! The issue has been reported on Adobe's bug tracker in 2008 and we can vote for them to fix it there: [https://bugs.adobe.com/jira/browse/FP-204](https://bugs.adobe.com/jira/browse/FP-204)

---

### Post by scotty64 on 2010-03-17
Have you tried preloading the V4L1 compatibility library ? That workaround does it for me with all cameras that have problems with Flashplayer 10+

Here is how you use it:
[http://ubuntuforums.org/showthread.php?t=1398279](http://ubuntuforums.org/showthread.php?t=1398279)

---

### Post by DPic on 2010-03-17
> **scotty64 said:**
> Have you tried preloading the V4L1 compatibility library ? That workaround does it for me with all cameras that have problems with Flashplayer 10+

Here is how you use it:
[http://ubuntuforums.org/showthread.php?t=1398279](http://ubuntuforums.org/showthread.php?t=1398279)

Thank you so much! This is the most elegant solution i've seen!

---

