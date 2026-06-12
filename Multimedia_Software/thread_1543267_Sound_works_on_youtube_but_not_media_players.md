---
title: "Sound works on youtube but not media players"
date: 2010-07-31
forum: Multimedia Software
---

### Post by mbyrd11 on 2010-07-31
The log in sounds will play but when i try to open up rhythmbox to listen to some music it says that its playing but there is not sound.

But when i go to Youtube I can hear audio.

Any suggestions to fix my problem?

Thanks in advance!

---

### Post by lidex on 2010-08-01
Try removing old config files. 
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
**Logout/in.**

Have you tried another sound app - exaile, etc?

---

### Post by lidex on 2010-08-01
Try removing old config files. 
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
**Logout/in.**

Have you tried another sound app - exaile, etc?
Try closing your browser and see if you get audio elsewhere.

---

### Post by mbyrd11 on 2010-08-02
Before I opened the terminal I Downloaded Exhaile and it worked. 
So I didn't remove anything yet.

Why Doesn't Rhythmbox or Totem Movie Player work?

---

### Post by lidex on 2010-08-02
Probably gstreamer. Follow this link:
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
Do parts 1 & 2.
You'll probably want this also:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by mbyrd11 on 2010-08-04
I did the instructions in the link and it didn't help anything.

I started looking at some things the other day and now i think that I've messed things up more because I can not seem to get the sound preferences to open.
I keep getting a message saying "Waiting for sound system to respond"

Also my sound indicator applet is always on mute even though vlc and exaile still work.

---

### Post by mbyrd11 on 2010-08-05
alright so I managed to fix my problems by renaming .pulse to another name and then Lucid made me a new .pulse and things work now :D

thanks for the help Lidex!

---

