---
title: "Which ALSA Mixer Recommended???"
date: 2010-10-24
forum: Multimedia Software
---

### Post by rockytoprsf on 2010-10-24
I just installed Lubuntu 10.04 on an old desktop. I tried to install 10.10, but got stopped by the CMOV issue. It has an old ISA Soundblaster 16 sound card, which I'm trying to get working. The Ubuntu Howto Setup Sound Cards article suggests using a sound mixer to help with setup. I don't see a sound mixer in the Lubuntu menu, and when I enter "alsamixer" at a terminal session, I just get a message indicating that no such program exists. Apparently, Lubuntu doesn't come with a sound mixer. When I go into Synaptic, I see what appears to be several sound mixers available (gnome-alsamixer, gamix, qamix, alsamixergui).

My question is: For Lubuntu, which ALSA mixer is recommended?

---

### Post by cavalier911 on 2010-10-24
alsamixer won't open with no sound devices installed.
For future reference:
Open terminal,to find executables location use the which or whereis command:
```
which alsamixer
```
should return
```
usr/bin/alsamixer
```
To install an ISA soundblaster compatible soundcard you have to configure lubuntu to load the **snd-sb16** kernel module.
```
sudo nano /etc/modules
```
At the bottom add **snd-sb16**
Close out nano with the following keystrokes:
Ctrl+X
y
enter
Reboot,open alsamixer,sound should work.

---

### Post by rockytoprsf on 2010-10-25
Hello cavalier911,

I followed your directions, and Voila!!!, Sound!!

Thanks for the help.

---

