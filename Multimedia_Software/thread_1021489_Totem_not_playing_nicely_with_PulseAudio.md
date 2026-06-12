---
title: "Totem not playing nicely with PulseAudio"
date: 2008-12-25
forum: Multimedia Software
---

### Post by jamesisin on 2008-12-25
I have gone through the PA fix-yer-problems page:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Everything seems to be working well with one exception.  For instance, I am able to hear a ring and connect in Skype while listening to Amarok.  Also, I can open and use Amarok if I am already on a call in Skype.

However, if I am listening to Totem Skype cannot ring and it is not possible to connect a call (audio error).

I suspect that I merely need to point Totem at PA, but I was not able to find anywhere in the application to accomplish that.

Anybody know how to fix this?

---

### Post by jamesisin on 2008-12-27
Anybody?

---

### Post by 2hot6ft2 on 2008-12-27
I believe skype uses OSS check the first link I saw skype there quite a bit.

Here are a few options to choose from from fixing pulse to disabling it and using asla, or replacing pulse with esound.

First fixing pulse (there are fixes in this thread for skype)
[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

Disabling pulse and using alsa (Before deciding to remove pulse you should read the warning here as to what the result could be).
[http://forumubuntusoftware.info/viewtopic.php?f=46&t=2179&start=0&st=0&sk=t&sd=a](http://forumubuntusoftware.info/viewtopic.php?f=46&t=2179&start=0&st=0&sk=t&sd=a)
and another one going the same route here
[http://ubuntuforums.org/showthread.php?p=6370902#post6370902](http://ubuntuforums.org/showthread.php?p=6370902#post6370902)

Replacing pulse with esound
[http://ubuntuforums.org/showthread.php?t=885437](http://ubuntuforums.org/showthread.php?t=885437)
A short version here. I suspect it will be modified.
[http://ubuntuextreme.blogspot.com/2008/12/how-to-fix-audio-in-intrepid-ibex.html](http://ubuntuextreme.blogspot.com/2008/12/how-to-fix-audio-in-intrepid-ibex.html)

There are more but this gives you some fixes that are being used.

---

### Post by jamesisin on 2008-12-27
The page I linked to in my original post does a great job of explaining how to get PA set up correctly.  It is working great.  So is Skype.

I really believe the problem is that Totem (Movie Player) is not pointing at PA, so Totem is not able to use audio while another application is using it.

I'm hoping to find out where Totem keeps its preferred audio settings.

---

### Post by jamesisin on 2008-12-29
A little help here?

---

### Post by jamesisin on 2008-12-30
Please?

---

### Post by jamesisin on 2009-01-01
Bueller?

---

### Post by GepettoBR on 2009-01-04
I'm not familiar with Totem's inner workings, but I too followed that same guide you linked to and MPlayer works great for me. Try using it instead to play your videos. It's a better app anyways, IMHO.

---

### Post by jamesisin on 2009-01-05
Thanks, but in a totally unrelated excursion into folly I have really hosed my system.  Not sure how as yet.  I have made a post here on a related thread:

[http://ubuntuforums.org/showthread.php?p=6490548](http://ubuntuforums.org/showthread.php?p=6490548)

I'm not clear where to go from here, but I know I cannot fix the Totem thing until I resolve this other issue.

---

