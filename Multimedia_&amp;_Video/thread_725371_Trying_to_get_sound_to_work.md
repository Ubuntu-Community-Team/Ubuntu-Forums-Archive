---
title: "Trying to get sound to work"
date: 2008-03-15
forum: Multimedia &amp; Video
---

### Post by liquidcross on 2008-03-15
I'm trying to get the sound to work on my Thinkpad R60. It's got the AD1981 HD audio chip, and it *used* to work fine when I originally installed Ubuntu...but now, it's completely dead, and no amount of tweaking settings seems to work. I've got alsa installed, and that's worked in the past, but it just don't won't give me any output now. Any thoughts?

---

### Post by Bubba64 on 2008-03-15
have you opened the volume control with a right click and made sure nothing is muted and every thing is shown and turned up. Personally I install the gnome alsa mixer it will show you every control, which like the the volume control will tell you if the right sound card is being used.

---

### Post by liquidcross on 2008-03-15
> **Bubba64 said:**
> have you opened the volume control with a right click and made sure nothing is muted and every thing is shown and turned up. Personally I install the gnome alsa mixer it will show you every control, which like the the volume control will tell you if the right sound card is being used.
Everything's unmuted and turned all the way up. I've got alsa installed, but alsaconf won't run from the terminal. Also, under Volume Control, two devices are showing up: HDA Intel (Alsa mixer), and Analog Devices AD1981 (OSS mixer). Neither one works.

---

### Post by Bubba64 on 2008-03-15
I am not an expert on this stuff so I am just relating what I have done on my own computer and what I have read on the forums is the listed alsa hd intel your actual sound card. Since you had sound and now you don't it is probably something I don't have a clue with. One thing I have noticed looking at these forums way to often is that no wireless and sound are the most common posts so you might find answers by searching for threads, I realize that any thing I suggest you might have already tried. Here is a thread that might help it looks like the 4th post has a terminal instruct that changes booting that hopefully may be your problem.
[http://ubuntuforums.org/showthread.php?p=1653926](http://ubuntuforums.org/showthread.php?p=1653926)

---

### Post by fenian on 2008-03-15
Have you tried [these instructions]("https://help.ubuntu.com/community/HdaIntelSoundHowto") ?

---

### Post by liquidcross on 2008-03-15
> **fenian said:**
> Have you tried [these instructions]("https://help.ubuntu.com/community/HdaIntelSoundHowto") ?
Just did. They didn't work.

---

### Post by fenian on 2008-03-15
You can try using the [script]("http://www.stchman.com/alsa_update.html") here to reinstall alsa.

---

### Post by liquidcross on 2008-03-15
> **fenian said:**
> You can try using the [script]("http://www.stchman.com/alsa_update.html") here to reinstall alsa.
Again, no dice. :(

---

### Post by liquidcross on 2008-03-16
I've tried every tutorial and fix i can find at this point; nothing's working at all.

Do you guys know of a way that I can completely purge any and all sound drivers from my system, then reinstall *only* ALSA and any driver required by the AD1981 card?

---

