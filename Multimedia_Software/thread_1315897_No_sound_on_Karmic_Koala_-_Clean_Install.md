---
title: "No sound on Karmic Koala - Clean Install"
date: 2009-11-05
forum: Multimedia Software
---

### Post by reef2dive on 2009-11-05
I have done a clean install of Karmic Koala on a MSI EX 310 Laptop with a Radeon HD 34xx and there is no sound. 
I went through the setup of Pulsaudio, as this fixed the problems previously. The difference is that in Karmic Koala there is no choice of which output that should be used ALSA, Pulseaudio or ESS.
I have checked the alsamixer to see if it is muted or not. 
The volume is set to full.

Any tips, or is it a bug and should be posted in launchpad?

---

### Post by reef2dive on 2009-11-06
OK, it is not a serious bug. After some additional browsing and playing with settings then the following solves the problem

The command 
sudo alsa force-reload
must be issued after the login.
When this is done some additional hardware shows up in the Sound Preferences window. Those settings I can then correct and get sound working.

The Internal Audio Analog Stereo does not show after reboot if the command 
"alsa force-reload" is not issued.

;)

---

### Post by darkwa on 2009-12-14
I have a toshiba satellite (tablet pc) and I was having no sound at all but, the command 
"sudo alsa force-reload" did it for me thanks!!

---

