---
title: "Sound problems after Skype"
date: 2008-05-03
forum: Multimedia Software
---

### Post by AmpersUK on 2008-05-03
&#65279;Greetings,

**I have lost my sound in Ubuntu 8.04.** I have been using a Creative X-FI card and since I moved to Ubuntu 8.04 this now works. I say works, and not worked, as the problem is not that I have an X-FI card as you will see below.

First of all then I log in to Ubuntu 8.04*** I hear the tone to sign in, and then the jingle as it opens up with my workspace.***

I installed Skype recently, and went in to change the sound in and out to my DECT Plantronics headset. Unfortunately this changed the whole sound all over the place even when closing Skype.

***I played around with the options for sound and then also lost sound through my Plantronics headset.***

I use rhythmbox for my music and now, alas, there is no music. :(

One very interesting thing here which has got me stumped is that I downloaded **Alsaplayer**, and it plays the music perfectly.

Can someone help me get my music back as this is important to me. I have a squeezebox fixed to my HiFi and intend to download SlimServer for Linux soon. This will enable me to play the music in the Lounge HiFi but it would be nice to play it on the computer in the office as well. 

And also, I'd like to know the reason behind the fact that the opening sounds work, and the little Alsaplayer works perfectly, but nothing else does.

---

### Post by altima on 2008-10-26
check out my post. I think we've got the same issue [http://ubuntuforums.org/showthread.php?p=6030326](http://ubuntuforums.org/showthread.php?p=6030326)

---

### Post by EnGorDiaz on 2008-10-26
> **AmpersUK said:**
> &#65279;Greetings,

**I have lost my sound in Ubuntu 8.04.** I have been using a Creative X-FI card and since I moved to Ubuntu 8.04 this now works. I say works, and not worked, as the problem is not that I have an X-FI card as you will see below.

First of all then I log in to Ubuntu 8.04*** I hear the tone to sign in, and then the jingle as it opens up with my workspace.***

I installed Skype recently, and went in to change the sound in and out to my DECT Plantronics headset. Unfortunately this changed the whole sound all over the place even when closing Skype.

***I played around with the options for sound and then also lost sound through my Plantronics headset.***

I use rhythmbox for my music and now, alas, there is no music. :(

One very interesting thing here which has got me stumped is that I downloaded **Alsaplayer**, and it plays the music perfectly.

Can someone help me get my music back as this is important to me. I have a squeezebox fixed to my HiFi and intend to download SlimServer for Linux soon. This will enable me to play the music in the Lounge HiFi but it would be nice to play it on the computer in the office as well. 

And also, I'd like to know the reason behind the fact that the opening sounds work, and the little Alsaplayer works perfectly, but nothing else does.

ok what you do is install pulse audio follow the instructions CAREFULY!...


[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

there is one bit thought about user groups and permissions find the executive file and execute it then after the permissions thing

---

### Post by markbuntu on 2008-10-29
To get skype to work properly with pulseaudio, do this:

[http://ubuntuforums.org/showthread.php?t=937323](http://ubuntuforums.org/showthread.php?t=937323)

---

