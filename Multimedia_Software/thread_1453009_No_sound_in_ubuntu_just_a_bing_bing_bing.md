---
title: "No sound in ubuntu just a bing bing bing"
date: 2010-04-12
forum: Multimedia Software
---

### Post by freaking on 2010-04-12
I have a HP Pavilion dv4 and I am kind of new to ubuntu. But i like it allot but the sound does not work . From when i start it to when i close it it just goes bip bip bip bip an annoying beeping sound and thats why i have to keep it on mute. PLEASE HELP

---

### Post by freaking on 2010-04-13
Please help ... I really want my ubuntu to work

---

### Post by hawthornso23 on 2010-04-14
What hardware are your sound preferences set up to use? It almost sounds like you are trying to route sound through the motherboard speaker.

---

### Post by lidex on 2010-04-14
Go to this page and install alsa-backports.
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")
Run this command in a terminal="Applications>Accessories>Terminal":
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
Add these lines at the bottom of that file:
```
options snd-hda-intel enable_msi=1
options snd-hda-intel model=hp-dv5

```
Save. Close. Reboot.

---

### Post by tyc on 2010-04-14
> **freaking said:**
> 
I have a HP Pavilion dv4 and I am kind of new to ubuntu. But i like it allot but the sound does not work . From when i start it to when i close it it just goes bip bip bip bip an annoying beeping sound and thats why i have to keep it on mute. PLEASE HELP


By chance, is that "HP Pavilion dv4" you have the same as a HP G60 or HP G70 series laptop? I ask this as I have a similar problem (no "bip bip bip ...", nothing, no sound what-so-ever) however I'm using a different OS; Slackware v13-64. 

I wonder if the answers suggested here may as well apply to Slackware users ... and for now, it appears that none of the Slackware "experts" know the anwer to this no sound and the HP G60/G70 series machines.

tyc

---

