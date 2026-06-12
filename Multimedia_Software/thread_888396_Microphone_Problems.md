---
title: "Microphone Problems"
date: 2008-08-13
forum: Multimedia Software
---

### Post by Peder_Erickson on 2008-08-13
I am currently unable to use any of my machine's microphone ports, I would love to be able to use a mic on my machine, but I need some help on getting that working

The volume control program says Volume Control:HDA NVidia (Alsa mixer)
I have all of the check boxes checked in the prefrences menu, and I have:

PCM, Front, Front Mic, Line-in, Microphone - Playback
Capture, Digital - Recording
Headphones - Switches
(Combo Box) Mic, Front Mic, Line In - Options 

So, if anyone could help, it would be really nice

I'm on Ubuntu 7.10

---

### Post by mad_prince on 2008-08-13
try this 
```
Run alsamixer
Unmute all the outputs by hitting &#8220;m&#8221;
Hit tab to go the capture settings
Highlight the &#8220;Mic&#8221; setting using the arrow keys.
Hit space to enable the microphone.
Highlight the &#8220;Capture&#8221; setting using the arrow keys.
Hit space to enable capture (note that just because you have volume bar
here doesn&#8217;t mean it is enabled).
Hit escape.
```

---

### Post by Peder_Erickson on 2008-08-13
I have no mic setting in the capture settings section,  I only have Capture, and Digital

I found that my lapop, which has a working mic, has a mic boost in alsamixer, and the gnome volume manager, but my desktop does not have this either

---

### Post by mad_prince on 2008-08-13
so use 'capture' instead of 'mic' I had same problem as you few hours ago (that's why I found your thread:)) and it helped me.

---

### Post by Peder_Erickson on 2008-08-13
Nothing at all from line in, the rear mic, or the front mic...

:confused:

---

### Post by mad_prince on 2008-08-13
are you sure you have enabled "capture" in capture settings by hitting space? Your capture settings tab should look simillar to this one:

---

### Post by Peder_Erickson on 2008-08-14
Yes, it's enabled

---

### Post by Macdelaney on 2008-08-16
I'm having a "similar" problem (posted here, [http://ubuntuforums.org/showthread.php?p=5603444](http://ubuntuforums.org/showthread.php?p=5603444) just in case :P), but when I press Space in the Alsamixer nothing happens, how do i know if its enabled or not?

---

### Post by mad_prince on 2008-08-17
look at my screen shot. If it is enable you can notice "captur" and "L" & "R". If it is disable there are only "---".

---

### Post by eggdeng on 2008-08-17
This works for me and others with Intel HDA.
[http://ubuntuforums.org/showthread.php?t=887697]("http://ubuntuforums.org/showthread.php?t=887697")

---

