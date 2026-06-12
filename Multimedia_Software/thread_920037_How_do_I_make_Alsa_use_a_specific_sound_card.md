---
title: "How do I make Alsa use a specific sound card?"
date: 2008-09-14
forum: Multimedia Software
---

### Post by killerclick on 2008-09-14
I have two sound cards, how do I make alsa use a specific card?

---

### Post by Yellow Pasque on 2008-09-14
```
asoundconf list
sudo asoundconf set-default-card PARAMETER
```

---

### Post by markbuntu on 2008-09-14
You can also get

asoundconf-gtk

which is a gui you can use to choose between sound cards.

---

### Post by killerclick on 2008-09-14
Thanks for your help! :)
Silly that they don't have the option to pick soundcards in System > Preferences > Sound...

---

### Post by markbuntu on 2008-09-14
Actually, you can do it there, your sound cards are listed.

---

### Post by killerclick on 2008-09-14
> **markbuntu said:**
> Actually, you can do it there, your sound cards are listed.

Yes, but if in System > Preferences > Sound I choose my soundcard instead of ALSA then I don't have sound in Flash. On my system Flash only plays sound through ALSA and ALSA was using the wrong audio card which I had no way of changing in System > Preferences > Sound.

I guess what I meant was there should be a way to configure ALSA (or whatever I'm using) right there in System > Preferences > Sound...

---

### Post by markbuntu on 2008-09-15
To put it bluntly, no. Sound allows you to choose the system sound server. The sound servers have their own configuration space as they should. 

If you are using pulseaudio, you can set the alsa default to pulseaudio and then choose which sound card output you want an application to play through with the PA Volume Control. It is very convenient.

You could even set up PA to use both of your sound cards at the same time. Alsa does not have this function successfully implemented due to sound card clock drift issues but PA uses a low latency resampling method that keeps clock drift minimized.

If you really want to get into this, you can read my guide and follow the links:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

