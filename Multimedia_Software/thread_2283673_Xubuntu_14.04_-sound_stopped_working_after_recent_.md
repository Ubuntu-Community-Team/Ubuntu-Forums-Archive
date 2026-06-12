---
title: "Xubuntu 14.04 -sound stopped working after recent upgrade"
date: 2015-06-23
forum: Multimedia Software
---

### Post by whitshade on 2015-06-23
Last week, I ran what was supposed to be a fairly routine update and lost sound on my Xubuntu box.  It still works using a media player like VLC or Parole, but I had to switch the audio device from High Definition Audio Controller Digital Stereo (HDMI) to the sound card (VT8237A/VT8251 Controller Analog Stereo) and I have sound in Abe's Amazing Adventure (?).  I have tried restarting alsa and restarting PulseAudio as well as uninstalling and re-installing these programs and restarting them.  I've also noticed that the volume control component on the Xfce Indicator Plugiin is gone.  Just to cover the obvious suggestions, my speakers are on and connected and I've checked PulseAudio Volume Control and my sound is not muted.  Any assistance is appreciated.  Thanks.

---

### Post by whitshade on 2015-06-23
**Problem solved! ** I updated the repositories and then ran a software update.  Then I restarted the system and forced alsa to reload and that fixed it.  I thought that I had done this once, but go figure.  I'm happy.  I would, however, like a reimbursement for the time I put in trying to solve this problem...:cool:

Here it is:

sudo apt-get update && sudo apt-get upgrade

reboot

sudo alsa force-reload

---

