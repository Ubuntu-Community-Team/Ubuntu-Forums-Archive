---
title: "Can't get Audigy SE sound card to work"
date: 2009-05-09
forum: Multimedia Software
---

### Post by spartan_87 on 2009-05-09
I installed Ubuntu 9.04 64-bit on my desktop which has a Sound Blaster Audigy SE sound card and ubuntu detects the card but I still have no sound. I went to System > Preferences > Sound and all the setting were on auto detect, but I have a built in sound card on my mother board so it is probably defaulting to that. I can change it to the ca0106 alsa driver but I still get nothing. I wasn't sure what to change the Default Mixer Tracks to: ca0106(Alsa mixer), Capture:ca0106(PulseAudio Mixer), or Playback:ca0106(PulseAudio Mixer)?? Anyone know?

Also when I run a lspci the Audio device says: nvidia corporation mcp55 high definition audio, which is my built in sound card so I guess it is still defaulting to the built in card. How do I get it to use my pci sound card?

---

### Post by spartan_87 on 2009-05-09
bump. Anyone know?

---

### Post by joshthewhistler on 2009-05-09
I have a similar problem, I have an Audigy SE and realtek built in audio and the sound card has never really worked correctly no matter how much I fiddled around with it.

---

### Post by markbuntu on 2009-05-09
The audigy driver is default digital output so you need to open the volume control and change the analog/digital switch. You may need to set the preferences in the volume control to see this switch so you can change it.

---

### Post by spartan_87 on 2009-05-09
Awesome, thanks. Well I got sound finally, I could never get Alsa to work but I did get OSS to work so I am using the CA0106(OSS) driver. And I checked the Analog Source box under volume control preferences. Can't get 5.1 surround sound but two speakers is better then nothing.

---

### Post by 500sd on 2009-05-10
how exactly did you get it working? 
i still have no sound with my audigy se...
i tried using the ca0106 oss driver but it didnt work. i also tried checking analog with no luck

---

### Post by azc on 2009-05-10
If you have on-board sound and an Audigy installed, try disabling the on-board sound in your BIOS.

(I had to do that on an old Gateway PC of mine.)

---

### Post by funeralthirst on 2009-05-10
> **markbuntu said:**
> The audigy driver is default digital output so you need to open the volume control and change the analog/digital switch. You may need to set the preferences in the volume control to see this switch so you can change it.

thank you. that got it working for my audigy 2zs card. also in the vol controls my speakers were set at no volume.

---

### Post by 500sd on 2009-05-10
i tried disabling onboard and still no luck
if its of any significance i have 3 of the same driver under preferences. i have 4 alsa audigy se drivers and 3 oss audigy se drivers.

---

