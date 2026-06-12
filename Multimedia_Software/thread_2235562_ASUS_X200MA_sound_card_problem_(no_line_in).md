---
title: "ASUS X200MA sound card problem (no line in)"
date: 2014-07-21
forum: Multimedia Software
---

### Post by Benjamin_Kovcs on 2014-07-21
Hi,

I'm unable to get my external headset and microphone working on my ASUS X200MA. The external speakers work fine, the sound gets redirected automatically. The machine has a combo jack for both input and output.
I've tried several ways mentioned on other forums:
adding [COLOR=#000000][FONT=Ubuntu Mono]options snd-hda-intel model=laptop-dmic[/FONT][/COLOR] to alsa-base.conf
This did not solve the problem.
I've also tried to change the profile of the sound card in KDE Control Center to stereo input with no results.
When I choose the external microphone in duplex or stereo input mode the signal indicator stays at 0.
I've set the input levels to maximum with KDE volume control (and also checked in alsamixer).

My ALSA information is located at [http://www.alsa-project.org/db/?f=2dc650589d89924f60dc5bb0e61ed177beb4e992](http://www.alsa-project.org/db/?f=2dc650589d89924f60dc5bb0e61ed177beb4e992)

---

### Post by Yellow Pasque on 2014-07-22
Remove the model= line from alsa-base.conf
Hopefully, this commit (found in Linux 3.16.x) fixes you up: [https://github.com/torvalds/linux/commit/13fd08a339f174840046d0b229f434c0a5ee9925](https://github.com/torvalds/linux/commit/13fd08a339f174840046d0b229f434c0a5ee9925)

Update to latest ALSA kernel code to try it:  [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

---

### Post by Benjamin_Kovcs on 2014-07-22
It did not solve the problem. It still uses the internal microphone, and I still can't change to the external manually.

---

### Post by Yellow Pasque on 2014-07-22
The only suggestion I have left is to try resetting pulseaudio config, and if that doesn't work, file a bug.
```
rm -r ~/.config/pulse
pulseaudio -k
```

---

