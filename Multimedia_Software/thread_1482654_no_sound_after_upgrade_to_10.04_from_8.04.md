---
title: "no sound after upgrade to 10.04 from 8.04"
date: 2010-05-13
forum: Multimedia Software
---

### Post by Denny Johnson on 2010-05-13
No sound.........no youtube, skype, rhythmbox, Ubuntu sounds ......nada.
For a while, each of these programs had sound, while others did not. Now nothing.
I've done a lot of searching, tried a few solutions, no joy.
It's possible that I did some damage in the flash plugin.
I'm lost, any experienced suggestions appreciated.
Here are some pulse screenshots, ALSA to follow:

---

### Post by Denny Johnson on 2010-05-13
and ALSA:
Thanks

---

### Post by WinterRain on 2010-05-13
Geez, another upgrade gone bad, what a surprise. Anyway, I would remove alsa and reinstall it. But just before reinstalling, do:
```
sudo apt-get clean && sudo apt-get autoremove
```

---

### Post by Denny Johnson on 2010-05-13
Thanks for the comeback, Rain.
I removed GNOME ALSA mixer, ran the code, installed Gnome ALSA mixer, and re booted........no joy.
Other suggestions?
Here's a terminal screenshot:

---

### Post by Denny Johnson on 2010-05-13
I thought I'd remove and install the Adobe Flash Plugin now.
It was no no longer installed.
Installed it..........still no joy.

---

### Post by Denny Johnson on 2010-05-13
Removed Skype and rebooted................no joy.

---

### Post by Denny Johnson on 2010-05-13
Rain.....I'm a novice........when you said remove ALSA, I went to the Ubuntu Software Center and removed the top listing from an ALSA search, that was GNOME ALSA mixer.
I've now gone to symantic done an ALSA search and see that I have lotsa ALSA stuff installed.
Reckon I didn't remove and install ALSA as you suggested.
How do I do that?
Here's what an ALSA search at Symantic shows:

---

### Post by Denny Johnson on 2010-05-13
and

---

### Post by JohnMac on 2010-05-14
I gather you checked the obvious, I noticed after I had installed Lucid the sound was muted. Check the speaker in the notifications panel to make sure it does not say "unmute"

---

### Post by Denny Johnson on 2010-05-14
Thanks John........I'm good there

---

