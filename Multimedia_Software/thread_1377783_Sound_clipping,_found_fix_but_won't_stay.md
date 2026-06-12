---
title: "Sound clipping, found fix but won't stay"
date: 2010-01-10
forum: Multimedia Software
---

### Post by Jerther on 2010-01-10
Hi!

Im using Ubuntu 9.10 64 bits. I have some problems with sound and my sound card is an old SB0220 (Sound blaster live 5.1 OEM)

It works very well in stereo mode. No problem at all.

However, in gnome-volume-control when I switch its mode to Analogue 5.1, the quality gets crappy, like it's clipping or something. The quality gets ok back when I switch the mode back to Stereo.

I did my homework and found a workaround. I installed gnome-alsa and just touched the PCM slider and voilà, sound gets normal. But as soon as I touch a volume slider in gnome-volume-control, the sound clips again.

Then I thought I could just remove the package and use only the ALSA mixer instead but Synaptics tells me it would also remove the whole gnome-desktop package.

I then tried to leave it that way, but as soon as I reboot, the sound clips again and I have to go to the ALSA mixer and touch the PCM slider again.

This problem seems to also happend in other distribs (Fedora) but I'd be happy just having the gnome-volume software leave the sound as the ALSA mixer sets it.

Any suggestion?

---

### Post by Jerther on 2010-01-11
I found this.
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/445849](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/445849)

Looks like a serious probem :|

---

