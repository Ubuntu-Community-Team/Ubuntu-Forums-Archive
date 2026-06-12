---
title: "Terrible DVD playback - Beating the dead horse"
date: 2009-01-05
forum: Multimedia Software
---

### Post by maxina on 2009-01-05
Sorry for bringing this up again but I have been through the gauntlet with the other posts, but nothing seems to fit with my case.

I have an Acer with a dual-core P4's (2.93 GHz), 2 Gig of Ram, and a 512Mb NVidia GEForce 7300 GT card. 

The system works smashingly, EXCEPT if I put anything into my optical drives. If I try to put a DVD in and use totem, the system COMPLETELY bags... I might as well go for a nap, its not coming back. If I use VLC, its "better", but still skipping every 5 seconds or so. All in all, Pretty painful to say the least. Looking at system monitor, neither the processor nor the memory is pinned, so I can only wonder where the bottleneck is???  FSB? Graphics Card? (and yes I am using the restricted drivers -- using the regular ones made no difference, other than giving me errors and causing me to be in low graphics mode)

This *feels* like a hardware issue, but then again, I am a windows guy, and I dont have a feel for the O/s quite yet...

---

### Post by jim_p on 2009-01-05
I think the optical drive is about to die soon, or at least does not drain all the power it needs to operate from the system.

---

### Post by thorgal on 2009-01-05
is it only when playing video content ? what about an audio CD, data DVD, etc ?

what about another OS ? did you buy your computer with e.g. windows ? if it is dual boot, did you try a video DVD under windows ?

---

### Post by atngplusultra on 2009-01-05
I know that personally, after I went from Hardy to Intrepid, my DVD drive seemed to do absolutely nothing.

After some amount of troublshooting, I got Totem to admit that there was some kind of corruption in the media stream, which I believed because VLC wouldn't play it either.

I have no clue what I did, but now VLC works just fine. So maybe your issue can be solved with just a little fiddling.

---

### Post by maxina on 2009-01-05
Hey all, thanks for the suggestions, 

I tried swapping out the DVD drive to eliminate the drive as a possible suspect. Unfortunately, the Windows O/S was DOA when I got the system. (hence why I went Ubuntu ;) ) 

Anyway, I guess what would be fantastic is: Is there any diagnostic tools out there that would help me find the bottleneck? 

Thanks again, 

Andrew

---

### Post by thorgal on 2009-01-06
you did not mention what happened when you use an audio CD or a pure data CD / DVD, i.e. anything except a video DVD. It is important to know whether it has to do with the drive itself or something else (mpeg2 decoding).

A test I would perform : get hold of an DVD image (iso file) and play it through VLC. VLC can play iso images just fine. Thus, you would not need the DVD drive as the iso image would sit on your hard disk. If the same symptoms happen when playing a DVD iso file, then your problem is elsewhere.

---

### Post by maxina on 2009-01-10
Hey All, its me again, 

So I had more time to play with the computer in question... To rule out that it was "just me" and a software (o/s) issue, I found this GREAT SCRIPT to make sure DVD playback will work

[http://www.hildoersystems.com/index.php/2008071862/enable-dvd-playback-in-ubuntu-in-one-command](http://www.hildoersystems.com/index.php/2008071862/enable-dvd-playback-in-ubuntu-in-one-command)

Someone Give this person a hug/beer whatever

Anyway, for every other machine this was a fix.. For this machine, no change...

Then I got a fabulous Idea: take my usb / IDE drive enclosure and jack the DVD player into it.. This will bypass the IDE drive controller

Well.. It works flawlessly, and without bagging the system.. So! Is there anything I can do to get around this (except perhaps an IDE controller card)?? Can this perhaps still be addressed with a driver? Or should I accept that its hosed? (and yes Im Canadian ;) )

Thanks Again

Andrew

---

