---
title: "VCD not playing on VLC and Movie Player"
date: 2010-01-01
forum: Multimedia Software
---

### Post by Sicadastra on 2010-01-01
Hello,

This is the first time I tried playing a VCD on my laptop and when I tried playing it on VLC, it indicated that an error, that it cannot read the file. I searched around the net for some solution and tried opening the VCD through the terminal to no avail. I tried switching to the Movie Player but it's the same. They play the initial 'Warning on illegal copying of the film, etc.' which lasts for about 15 seconds but after that, it won't play at all.

Can anyone assist me with this? Thank you.

---

### Post by Jose Catre-Vandis on 2010-01-01
> mplayer vcd://

Does this work? If not what output do you get in the terminal?

---

### Post by Sicadastra on 2010-01-01
> **Jose Catre-Vandis said:**
> Does this work? If not what output do you get in the terminal?

I tried the command and it produced this reply:

The program 'mplayer' is currently not installed.  You can install it by typing:
sudo apt-get install mplayer-nogui
mplayer: command not found

Weird because I have the Movie Player (the one installed with Ubuntu) unless it's another movie player it's referring to.

---

### Post by xc3RnbFO8P on 2010-01-01
Try:
> totem vcd://
or install SMPlayer

---

### Post by Sicadastra on 2010-01-01
> **Ringi said:**
> Try:

or install SMPlayer

It opened the Movie Player, all right, but it's still stuck with the Warning part only.

I am hesitant to install another media player since I already have the Movie Player and VLC but thanks for the suggestion; I might look into it.

---

### Post by alexfish on 2010-01-01
Hi

which version of Ubuntu are you using

---

