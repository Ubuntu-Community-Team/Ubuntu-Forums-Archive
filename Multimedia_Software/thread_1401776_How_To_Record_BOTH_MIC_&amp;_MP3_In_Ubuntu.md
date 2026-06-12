---
title: "How To Record BOTH MIC &amp; MP3 In Ubuntu?"
date: 2010-02-08
forum: Multimedia Software
---

### Post by AlexanderDGreat on 2010-02-08
Hi, I'm really confused. All I can record in my computer using The Sound Recorder in Jaunty is 1. It's either MIC or an MP3. You have to turn off one to keep the other and vice versa. How do you record both?

PS I did some homework and they said I need to install a mixer. But I've tried alsamixer, gnome-alsamixer, kmix, jack, they don't the mixers that I need.

PPS I'm recording from Sound Recorder and gtk-recordmydesktop.

Thanks for reading.

---

### Post by tgalati4 on 2010-02-08
I think muse will work:

sudo apt-get install muse

If you already have an mp3 track and you simply want to sing over it, then use audacity:

sudo apt-get install audacity

---

### Post by AlexanderDGreat on 2010-02-10
Nope, muse still didn't work, it says MusE failed to to find a Jack audio server.

No, actually I'm doing a screencast. I want to be able to speak using a microphone while playing some music, this will be done using recordmydesktop, but can't get around it. It's tough.

---

### Post by bcschmerker on 2010-09-04
> **AlexanderDGreat said:**
> ...All I can record in my computer using The Sound Recorder in Jaunty is 1. It's either MIC or an MP3. You have to turn off one to keep the other and vice versa. How do you record both?...

Thanks for reading.I have a similar problem with my Creative Laboratories® SB0350 under 10.04 Lucid.  When I ran 8.04.* Hardy, I had no trouble recording MP3 direct from analog using GNOME Sound Recorder and any combination of audio sources from the SB0350's Recording/Streaming bus.  Now, in 10.04, Sound Recorder can handle OGG but not MP3.  What need I double-check concerning multimedia library packages?

---

### Post by Oltsak on 2010-09-06
I have the same problem. I tried to ask this also elsewhere: [http://ubuntuforums.org/showthread.php?t=1330728&page=3](http://ubuntuforums.org/showthread.php?t=1330728&page=3). The script provided there works, but it does not solve this problem. 

Previously (with Fedora and older Ubuntu) it was possible to record from many sources at the same time. E.g one source is some  application and another source is line-in. This worked when 'mix' and 'rec-capture' was selected from alsamixer. But, as said above, it is not possible to select the both at the same time anymore :( 

It would be nice to get this working without removing Pulseaudio, because it seems we have to live with it...

---

### Post by elliotn on 2010-09-06
Also try Jokosher

---

### Post by Oltsak on 2010-09-07
> **elliotn said:**
> Also try Jokosher

Problem here is that this used to work with command line tools and alsamixer without any headache. These tools cannot be used as before anymore. So it is not about multitracker tools, but mixer/pulseaudio settings I guess...

---

### Post by cchhrriiss121212 on 2010-09-07
You can do this with jack, not an ideal solution but it is compatible with recordmydesktop and you can use timemachine as a simple recoding device. You also would not need to remove pulse or anything else.

---

