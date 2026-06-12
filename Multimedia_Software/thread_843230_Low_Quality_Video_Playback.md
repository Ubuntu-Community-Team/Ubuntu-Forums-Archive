---
title: "Low Quality Video Playback"
date: 2008-06-28
forum: Multimedia Software
---

### Post by Aibynn on 2008-06-28
I dual boot between Windows and Hardy Heron. I'm trying to use HH more often, but even simple things like video playback are causing me headache.

I have a Quad Pentium, 4 GB of RAM and an NVidia 8800 GTX. I have a nice big 27" dell monitor running at 1920x1440.

I've tried as many drivers/options as I can think of (far too many to mention here) and I'm STILL getting shearing and low quality output of simple video files. 

The same video files, played under ANY video player in Windows look great. Under Ubuntu, whether I use VLC, Totem, Movie Player, whatever, generally looks badly rendered (edges aren't smooth) and I get shearing if I size the video to anything larger than about 1/2 screen (not always, but when anything fast is happening). 

The best results I'm getting are from Kaffine, but they're still not up to snuff.

Any help would be great, because this is obviously frustrating.

Cheers!

---

### Post by Pjotr123 on 2008-06-28
1. Install the restricted driver:
[http://ubuntutip.googlepages.com/thefirstthingstodo](http://ubuntutip.googlepages.com/thefirstthingstodo)
(number 2 )

2. Disable visual effects:
[http://ubuntutip.googlepages.com/tipsandtweaks](http://ubuntutip.googlepages.com/tipsandtweaks)
(number 5 )

That should do the job just fine.  :-)

---

### Post by Aibynn on 2008-06-28
Thanks for that, unfortunately no go.

I was already using the latest (stable) drivers and visual effects on/off makes no difference.

---

### Post by markbuntu on 2008-06-28
Try this, in Advanced Deskyop Effects Settings or with the Compiz Settings Manager (the same thing actually) in the General section make sure that unredirectfullscreenwindows is checked. 

Also, make sure you have direct rendering (dri) working. var/log/Xorg.0.log should have a line in there about dri enabled or successfully installed or something like that.

Also, try setting vlc to use Xv. That should give you direct rendering in full screen. It may also cause a crash so be prepared for that.

Other than that, you may have to fool around with the setting options for the nvidia driver. I am using ATI so I don't know how you would go about that for nvidia. But I do know the 8800 should not be doing what it is doing to you.

---

### Post by amtam on 2008-06-28
In my opinion, you will never get the same quality of video-playback in Ubuntu as you get in Windows. Somehow, video in Windows almost alway looks better. If it's better drivers, filters, software, I don't know.

---

### Post by markbuntu on 2008-06-28
I get excellent video quality with miro and vlc. Full Screen HD video is quite nice on my 24 inch monitor. I set them to use Xv which gives direct rendering of 3D, textured video, adjustable anti aliasing, ansiotropic filtering, mimap detailing, and the Catalyst AI that is used in the Windows version. But then again, I am using an ATI card with the latest ati driver.

---

### Post by Aibynn on 2008-06-28
MarkUbuntu, what can I say...

I did those few things and the results are *tremendously* better. Not a little, but an absolute s%#$load. Have only tried it with VLC, but that's just fine with me. 

Not sure exactly what did it (whether it was just one thing or the combination), but I'll try to find out.

Thanks again!

---

### Post by markbuntu on 2008-06-29
Glad I could help you out,

best regards.

You should post how exactly you did it so others can find out and then:

You should mark this thread as solved.

---

### Post by mindhaq on 2008-09-18
I just came to this thread after recognizing a significant quality difference  playing a streamed WMV video in both Vista (MSIE 7, WMP) and Ubuntu (FF, VLC). On Vista, the full screen was much sharper and had almost no artifacts.

After enabling Xv rendering in VLC, this became much better and is on par now I think.

This is done in VLC settings - Video - Output modules, with "advanced options" checked.

The other recommendations (dri and unredirectfullscreenwindows) were already activated before.

So thanks to MarkUbuntu from me as well :)

---

### Post by Skeleton_Eel on 2008-09-18
i think if you changed video outputs driver , the problem can solve

try xv , gl/gl2 or sdl driver

[IMG]http://img329.imageshack.us/img329/9523/screenshotsmplayerprefekf8.png[/IMG]

i'm useing smplayer :)

---

