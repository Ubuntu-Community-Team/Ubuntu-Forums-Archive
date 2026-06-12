---
title: "No sound in Java apps"
date: 2009-07-25
forum: Multimedia Software
---

### Post by Razmear on 2009-07-25
I just installed 9.04 on my wife's PC. I have sound working for effects and for music and movies, but not for Java apps like the games on Pogo. 
To get the sound working I had to change the default the default device in Sounds, then to get the volume control working change it there twice, once for device, then a right click and preferences as well. 
I'm guessing there is yet another place I need to change from the default card to the working card that I haven't found yet. Any tips would be appreciated. 

Thanks,
eb

---

### Post by nonewmsgs on 2009-07-26
java and pulse audio don't seem to play nice together :(

only the java prog or everything else can have sound...it seems like whichever is opened first.

---

### Post by igorzwx on 2009-07-26
Why not try OSS4 in another partition, for example

---

### Post by Yellow Pasque on 2009-07-26
Java will use ALSA directly, and not Pulseaudio, so it tends to want exclusive access to the sound hardware. I've seen some people start Firefox with this command to work around:
```
padsp firefox
```

---

### Post by Razmear on 2009-07-27
I got it fixed. There were a few other issues but this one came down to having to disable the integrated sound card in the BIOS. Once I disabled it the long list of options for sound cards got much shorter and sound started to work again for all apps. 
Prior to disabling on the BIOS I killed pulseaudio and the SWFMozzila plugin, so those might be steps needed to. YouTube vids would not play because of the SWF plugin, nuking that let Adobe take over (they were both installed). 

eb

---

