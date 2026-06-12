---
title: "amarok problem"
date: 2007-11-16
forum: Multimedia &amp; Video
---

### Post by cc93 on 2007-11-16
hello amarok doesnt

---

### Post by Biggus on 2007-11-16
> **cc93 said:**
> hello amarok doesnt

amarok doesn't rok?

---

### Post by cc93 on 2007-11-16
EDIT: amarok doesn't produce sound

---

### Post by Stochastic on 2007-11-16
That's most likely an issue with your xine (amarok's sound engine).

---

### Post by cc93 on 2007-11-17
how can I fix it?

---

### Post by Stochastic on 2007-11-17
I don't know, and most people in this section of the forums probably won't be that well versed with xine as it's more intended as a media playback app see [http://www.xinehq.de/](http://www.xinehq.de/). You'll find more luck posting in the Multimedia & Video forum.  I'm by no means a moderator, it's just a suggestion.

---

### Post by cc93 on 2007-11-17
thx :(
but no music player produce sound except movie player !

---

### Post by meindian523 on 2007-11-17
can you give specs about your sound card?or are you trying to play only mp3s??Does Movie Player play mp3s?

---

### Post by forestpixie on 2007-11-17
try installing libxine for it, in fact have you installed any codecs at all? did they work before but not now? try giving people a bit more information.

```
sudo apt-get install libxine1-ffmpeg
```

---

### Post by cc93 on 2007-11-17
chris@chris-desktop:~$ sudo apt-get install libxine1-ffmpeg
[sudo] password for chris:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libxine1-ffmpeg is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.



:(:(

---

### Post by cc93 on 2007-11-17
no tried to use amarok and other players for fisrt time
i havent installed any codecs

---

### Post by meindian523 on 2007-11-17
Install the gstreamer-ugly plugins from Synaptic and try again....

---

### Post by cc93 on 2007-11-17
I found and installed them but nothing again
in sound preferences AUDIO CONFERENCING >SOUND CAPTURE  it appears this ---> error screen shot :   [IMG]http://i5.tinypic.com/71x2009.png[/IMG]

I don't know  if porblem comes from here :S 
BTW i have 2 sound cards but on is broken so i use the other one

---

### Post by forestpixie on 2007-11-17
when you say you have a broken sound card - is it an onboard card or a pci card - if you've got two and one works I'd guess that's what the problem. Alos are you able to specify in the bios which sound card.

---

### Post by cc93 on 2007-11-17
How?

---

### Post by forestpixie on 2007-11-17
well that's what I asked you I guess - some let you choose apparently although I can't. I think you need to deal with the broken soundcard.

---

### Post by cc93 on 2007-11-18
when I start up my pc in login window  must play a sound right? sometime this sound doesn't play  and amarok doesn't produce sound

---

### Post by forestpixie on 2007-11-18
I assume that before you had a probelm you weren't using both sound cards - is that the case?
if you know you've got a broken sound card you need to deal with that I think. If it's the onboard one you should be able to turn it off with the bios. If it's a broken pci one remove it. It looks like you have a software issue as well but that could be caused by the hardware issue.

---

### Post by cc93 on 2007-11-18
THANKS!  i will remove my broken card from my pc

---

