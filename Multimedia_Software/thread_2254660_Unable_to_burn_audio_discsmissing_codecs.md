---
title: "Unable to burn audio discs/missing codecs?"
date: 2014-11-29
forum: Multimedia Software
---

### Post by pierluigi.petesamp on 2014-11-29
Hi, I'm relatively new to Lubuntu(14.4.01) and I'm really satisfied so far. But, when trying to make an audio cd for my car stereo, the app(Brasero o Xfburn) shows a message, noticing me that these mp3s aren't audio files.
Now, I can't paste the exact tenor of the error, but I think it's about codecs.
I made several attempts to download them, to no avail.
Can anybody help me with that?

Thanks

---

### Post by uRock on 2014-11-29
Hello and welcome to the forums. 

To fix this problem, you will need to go into the software center, then search for and install the** lubuntu-restricted-extras** package. This will give you the needed codecs to use MP3s.

This can also be accomplished by opening a terminal, then copying and pasting the following command into the terminal and hitting enter.```
sudo apt-get install lubuntu-restricted-extras -y
```If this doesn't help, then please feel free to let us know.

Cheers & beers,
uRock

---

### Post by pierluigi.petesamp on 2014-11-29
Hi, thank you. It's something that I've already tried, with no results.

---

### Post by ajgreeny on 2014-11-29
> **pierluigi.petesamp said:**
> Hi, thank you. It's something that I've already tried, with no results.

What exactly do you mean by that?
Have already installed that package or not; was the problem installing that package, or was it that it still does not allow you to use mp3 files?

Can you play the mp3s with an audio player such as gnome-mplayer, audacious, or whatever Lubuntu 14.04 uses?

---

