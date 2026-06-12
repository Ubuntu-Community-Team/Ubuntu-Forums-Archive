---
title: "Rhythmbox and pulseaudio problem"
date: 2010-07-14
forum: Multimedia Software
---

### Post by apesa on 2010-07-14
I have a problem with Rhythmbox working. I am on Lucid with current updates. I muted the system volume as I took a phone call, when I went to unmute I had no sound out of the speakers or earphones. Restarted the machine and same thing. If I remove all pulseaudio pkgs it works but the System->Preferences->Sound app can't find the sound system. If I reinstall pulseaudio I get no sound and the playback speed is super fast.

Looking for some ideas,
Pat

---

### Post by jandugacek on 2010-07-15
The video is probably also super fast with no sound. I have the same problem, and it seems that it was never solved. It is said that logging in as another user should help. I am waiting for an upgrade that fixes it, because uninstallation of some packages helped, but only until running update manager.

---

### Post by apesa on 2010-07-15
Actually, if I uninstall pulseaudio everything including the sound works fine. But with Pulseaudio installed Rbox does not play anything back and video works but no sound. So I am leaving Pulseaudio uninstalled. This all was working fine until I muted the system sound during a phone call. Once I unmuted the volume control it was broken... I was listening to Rbox at the time.

Thanks for the reply.. I searched up and down the internet and these forums for what I am experiencing and have found nothing. So far I have uninstalled/reinstalled Rbox and pulseaudio pkgs from Synaptic and command line.

I am running Lucid 64 bit upgraded from 9.10 and this would not be the first Lucid challenge I have experienced. Support for the Radeon HD 4890 using catalyst has been a challenge.

Pat

---

### Post by apesa on 2010-07-16
Update: [HOW-TO: Pulseaudio Fixes]("http://ubuntuforums.org/showthread.php?t=789578") I found something here that worked for me. Namely libsound2-plugins and padevchooser

---

### Post by lidex on 2010-07-17
Also on a system upgrade you can have old configuration files causing these issues. To remove: Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
**Logout/in.**

---

### Post by jandugacek on 2010-07-20
Hooray, it helped! Thanks.

---

