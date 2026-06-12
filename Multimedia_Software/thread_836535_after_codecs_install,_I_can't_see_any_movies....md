---
title: "after codecs install, I can't see any movies..."
date: 2008-06-21
forum: Multimedia Software
---

### Post by kboy on 2008-06-21
i've installed an ubuntu 8.04 version a couple of hours ago, plus i've installed the codecs by using the wiki hardy heron guide.
now i can't see any picture in the movie files, not even in the ogg example file that came with the liveCD.
I can hear everything just right but no picture!!!

i've removed the codecs but the problem remains.
what to do??? i never had this problem in the gusty version of ubuntu....

---

### Post by Pjotr123 on 2008-06-21
Apply this how-to:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

---

### Post by kboy on 2008-06-21
i went over the guide and did everything that in guide, but it didn't work.
i still have the same problem, i hear everything but no picture. I even tried different media players.... any other suggestions???? the last thing i want to do is to install ubuntu all over again!!!
thanks!

---

### Post by mc4man on 2008-06-21
you may at some point want to post some particulars - laptop or desktop, video adapter (ati ,nvidia, onboard), whether your using compiz , adv. desktop effects, video driver (open source, restricted, proprietary.)
You could try - for totem - system -> preferences -> multimedia systems selector (or run gstreamer-properties ) and under video tab -> default output -> plugin choose the one ...(no Xv) 
 For vlc go to Settings-> Preferences-> enable Advanced options -> Video-> output modules, select the "X11 video output in the drop down.
related thread [http://ubuntuforums.org/showthread.php?t=811484](http://ubuntuforums.org/showthread.php?t=811484)

---

### Post by kboy on 2008-06-21
thanks allot!!!!
it worked great!!!!!!

---

### Post by shebuwa on 2008-06-21
> **Pjotr123 said:**
> Apply this how-to:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

THANK YOU sooooooo much! ):P

Took me a while, .... but that sure did the trick.

OK ... I will be leaving for now. I have been reading here for days, and I have now got Ubuntu Hardy up and running, flawlessly I might add :), on my OLD DELL LATITUDE C610 - Mobil Intel Pentium III CPU with a 40 gig HD and 512mb ram. I am amazed by how swift and stable this OS is on my old laptop. Truly an amazing OS.  

This is now a Linux only machine. No more dirty windows for me.

I just had to say thank you. I will try not to bug you people, with any silly questions, until I finally do get stumped.  

Thanks again Pjotr123, and all the rest of you too!

bye for now

Lynn

---

