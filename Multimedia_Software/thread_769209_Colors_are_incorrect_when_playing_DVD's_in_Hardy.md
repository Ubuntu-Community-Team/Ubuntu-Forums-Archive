---
title: "Colors are incorrect when playing DVD's in Hardy"
date: 2008-04-26
forum: Multimedia Software
---

### Post by employeeno5 on 2008-04-26
Hardy has been a real pleasure so far. I've been using it since the beta

The one small issue I haven't managed to work out yet though is that though DVD's play with menus and everything the color is always incorrect.

It might even be inverted. People are blue though. Lots of things are blue. This is the same no matter what player is use. 

My video card is a NVIDIA GeForce 8400M.

I'm feeling a little clueless here. I'm surprised I'm not finding anyone else with this issue searching the forums.

Any ideas? Many thanks.

---

### Post by cor2y on 2008-04-26
its a bug in the closed source nvidia drivers adjust the hue color settings of your video player of choice.
In Totem go to Edit->Preferences the Display tab and set the Hue to either max or min.

---

### Post by employeeno5 on 2008-04-26
Superb. Thanks so much. I'd actually gone looking for color adjustment settings previously, I don't know how I missed the hue there.

Again, many thanks.

---

### Post by sioc on 2008-05-09
Hi !

I experienced this problem too... really annoying !

As a first solution, I found a stupid workaround : you can go in nvidia-settings, choose the "X Server XVideo settings" line (may not be the exact name). There you can adjust contrast/brightness, but not hue. I suspect the control exists but doesn't appear in the tool... so move randomly one of the sliders, then push the "Reset hardware defaults" button... and then, magically, it can solve the color problem with you DVD playback.
This solution is pretty messy, since you have to reproduce the entire process each time ... but it can help since all video player doesn't give access to a hue setting...

But I may have another trick :

This driver bug seems to be related to another one you may have experienced too, because it relates to color and effects on display :
[http://ubuntuforums.org/showthread.php?t=772408](http://ubuntuforums.org/showthread.php?t=772408)

The given hack worked fine for me (for the pink glow at least), and seemed to solve the issue with DVD colors in the same time... I haven't tested it fully and extensively, I just tried it yesterday and after this the DVD playback was OK, but it might be some random coincidence...

Just hope this may help... 

;)

---

### Post by spyder0080 on 2008-05-10
thanks sioc! it worked!

---

### Post by Portable_Jim on 2008-07-07
> **cor2y said:**
> its a bug in the closed source nvidia drivers adjust the hue color settings of your video player of choice.
In Totem go to Edit->Preferences the Display tab and set the Hue to either max or min.
Thanks. Works on Hardy 64-bit.

---

### Post by pjbgravely on 2008-07-19
I had the color inversion and fixed it with the work arounds. The result was a normal but degraded picture.

Looking through the bug reports I see there are 3 different causes for the same problem. 

Sometimes the problem is caused by installing gxine. Something in the configuration files is doing it. The fix is to completely remove gxine. 

sudo apt-get purge gxine

Restart X and if that was the cause your problem will be fixed without work arounds.

Paul

---

### Post by killalot100 on 2008-08-03
thanks that worked

---

### Post by meihua on 2008-08-31
Just to thank cor2y   for help . Setting hue to minimum cured incorrect colours with hardy heron

---

### Post by maynoth on 2008-09-01
Thanks!  I had an issue with mp3 playback so I installed gstreamer, that fixed it, however then all my colors inverted in videos ugg!,  uninstalling gxine seems to work for the colors issue.   

> **pjbgravely said:**
> I had the color inversion and fixed it with the work arounds. The result was a normal but degraded picture.

Looking through the bug reports I see there are 3 different causes for the same problem. 

Sometimes the problem is caused by installing gxine. Something in the configuration files is doing it. The fix is to completely remove gxine. 

sudo apt-get purge gxine

Restart X and if that was the cause your problem will be fixed without work arounds.

Paul

---

### Post by me121 on 2008-09-13
cool, completely removing gxine fixes it!

---

### Post by kewljedi on 2008-09-19
Thanks!!! removing gxine and restarting x did the trick!!!

---

### Post by adam_kimber on 2008-10-11
> **cor2y said:**
> its a bug in the closed source nvidia drivers adjust the hue color settings of your video player of choice.
In Totem go to Edit->Preferences the Display tab and set the Hue to either max or min.


You are a STAR! :KS:KS:KS:KS:KS:KS :guitar: I have now fixed a problem that has been annoying me for ages! :D

---

### Post by persev on 2008-11-13
Thanks cor2y!

---

### Post by punkybouy on 2009-04-16
> **cor2y said:**
> its a bug in the closed source nvidia drivers adjust the hue color settings of your video player of choice.
In Totem go to Edit->Preferences the Display tab and set the Hue to either max or min.
Thanks Cor2y!!!!!!!!!!!!!!!  That worked.

---

### Post by godbacchus on 2009-11-08
> **sioc said:**
> push the "Reset hardware defaults" button... and then, magically, it can solve the color problem 

You. are. awesome.

- ODB

---

