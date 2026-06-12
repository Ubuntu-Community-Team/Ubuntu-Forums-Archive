---
title: "Desirable Totem (Movie Player) dependencies interfere with Miro Installation"
date: 2011-05-22
forum: Multimedia Software
---

### Post by promet on 2011-05-22
Hello,

I was experiencing problems in Totem (Movie Player) seeking through some mp3 files. This problem, luckily, was solved (as per [this launchpad bug post]("https://bugs.launchpad.net/ubuntu/+source/totem/+bug/750290")) by swapping the package:

*gstreamer0*.*10*-*plugins*-*bad*[I]

for the package:

[/I]*gstreamer0*.*10*-*plugins*-*bad*-*multiverse*

The only problem being that the package Miro [I]**requires**:

[/I]*gstreamer0*.*10*-*plugins*-*bad*

So, this makes me have to choose between Totem and Miro. I'd like to use both, fully enabled. Does anyone have any thoughts about this? I'd appreciate it.

Thanks!

---

### Post by mc4man on 2011-05-23
Try re-installing gstreamer0.10-plugins-bad, the 2 plugins aren't an either or, they provide different things.

---

### Post by promet on 2011-05-23
> **mc4man said:**
> Try re-installing gstreamer0.10-plugins-bad, the 2 plugins aren't an either or, they provide different things.

Hey mc4man, 

I appreciate the reply, but "gstreamer0.10-plugins-bad" cripples Totem on my install (the aforementioned seeking issue). If I had to choose between the lesser of two evils, I will choose to have mp3 seeking, that's pretty important for me.

My goal would be to find a workaround where I can have Totem execute seeking ***and  ***have the ability to install Miro. I hear where you're coming from though...

Cheers!

---

### Post by mc4man on 2011-05-23
Interesting - must be something about certain mp3's
seeking in mp3's is provided by the bad or fluendo plugin, don't see that the bad multiverse provides anything here 
(multiverse variants mainly provide encoding supports

If you come across a link to an mp3 that shows this post a link..

---

