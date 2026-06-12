---
title: "Sound not working"
date: 2010-04-07
forum: Multimedia Software
---

### Post by Minty :) on 2010-04-07
I just installed Ubuntu and i noticed that the sound wasn't working. Everything else works ; wireless..., but not the sound

I installed all of the codecs (i think) and it shows that i have a sound device in the sound menu, but no sound comes out of the speakers or out of headphones

I have Ubuntu 9.10
HP Pavillion DV6

---

### Post by lidex on 2010-04-08
You'll need a terminal for this="Applications>Accessories>Terminal"
Enter these commands, one at a time, and press enter. Input your user password when prompted. It will not display.
```
sudo apt-get update
sudo apt-get upgrade
sudo update-grub
gksudo gedit /etc/modprobe.d/alsa-base.conf
```

That last command opens a file for editing. Append these lines at the bottom of said file:
```
options snd-hda-intel enable_msi=1
options snd-hda-intel model=hp-dv5

```
Save. Close. Reboot. Check mixer levels in alsamixer:
```
alsamixer
```
Use arrow keys to navigate/edit.

---

### Post by Minty :) on 2010-04-08
i tried alsomixer and put it all the way up

and i tried "aplay -l" and it came up with a list of 3 diff devices

---

