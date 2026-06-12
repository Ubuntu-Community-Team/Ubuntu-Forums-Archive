---
title: "Connexant/NVidia audio just randomly stopped working?"
date: 2011-03-18
forum: Multimedia Software
---

### Post by RedPenguin on 2011-03-18
My Compaq Presario F739WM laptop has a Connexant HD Audio/NVidia MCP51 (reported by lspci) sound card.

Ubuntu has always supported the card with no problem except the random popping noise but then I found a work around for that.

Now for some reason, when I first turn on my computer and at login screen I can hear Ubuntu noises, yet seems once I login, no more sound or sometimes the successfully logged in sound.

The only changes that I have since the sound worked, was I installed pulseaudio but that caused no problems with that. The other change was a few kernel upgrades and other packages through normal update manager.

I have checked that snd_hda_intel driver was loaded in the kernel and in alsa, all seems well.

Pulse detects audio output in it's meter.

I also tested the sound card to make sure it wasn't bad, in Windows 7 (dual boot) and it wokrs perfectly.

---

### Post by lidex on 2011-03-18
Try resetting your pulse configuration.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Logout/in.**

No joy? 
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by RedPenguin on 2011-03-19
Thank you so much, your clearing of PulseAudio worked perfectly, only problem was, Logout/in wasn't enough, a full restart was required. Either way, it worked.

I am surpised I never seen anything like your suggestion online searching Google, so definitely thanks.

EDIT: I don't know what's going on, it suddenly stopped working. I guess I can uninstall PulseAudio, but as far as I know, it's really the only way to record Stereo Mix which I do once in a while.

EDIT #2: I give up, now it seems to randomly be working again after I left my laptop on to do stuff while I was gone.

---

### Post by lidex on 2011-03-20
Post the alsa-info-script output and I'll take a look at it. Are you using suspend/resume? Sometimes the audio chip does not re-initialize after suspension. If it goes out again see if reloading alsa brings it back:
```
sudo alsa force-reload
```

---

### Post by RedPenguin on 2011-03-23
I almost never use suspend/resume, but so far the audio is not going out, but I will give that a try if for some reason it does manage to go out again.

---

