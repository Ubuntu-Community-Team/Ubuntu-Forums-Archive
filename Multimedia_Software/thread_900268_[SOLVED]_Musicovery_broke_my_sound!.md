---
title: "[SOLVED] Musicovery broke my sound!"
date: 2008-08-25
forum: Multimedia Software
---

### Post by zenithdave on 2008-08-25
Hello i tried Musicovery (shockwave streaming audio) last night in firefox 3.01 it then hung up firefox so i had to force reboot, after that i have no sound!!

Everything was working fine before.

I have Midiman delta 44 sound card running on the ALSA drivers

The hardware is seen and configured using 'lspci' so it seems if the Shockwave app has left in a nasty state.

Using the Test function in the sound/alsa configure section gives an error could not open audio device for playback.

Please help i dont know where to start. thanks

ETA in the user logs it does indeed mention lots of initialisation failures related to PulseAudio and alsa

SEE LOG BELOW
Aug 25 09:36:29 phooeyinc-desktop pulseaudio[6000]: module.c: Failed to load  module "module-alsa-source" (argument: "device_id=2 source_name=alsa_input.pci_1412_1712_sound_card_0_alsa_capture_0"): initialization failed.

---

### Post by zenithdave on 2008-08-27
Bump! anyone ?

---

### Post by zenithdave on 2008-08-28
This is solved:lolflag:

After hours of searching i just uninstalled Pulseaudio server with synaptic! The drums came up at boot and i was elated.

Thats 2 things i have switched off now and cured major problems.

Sketchup crash cured by switching off desktop effects (open gl issues) and major sound probs by killing Pulseaudio

I dont mind my machine being used to test stuff thats why i have Proposed updates on, just wish i knew more about it.

Loving ubuntu

---

### Post by markbuntu on 2008-08-28
If you want to know more about sound and how it works, especially alsa with pulseaudio and jack, you can read my guide:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by zenithdave on 2008-08-29
Ok thanks for that will have a good read, this is my main area of interest as i do a bit of music production.

It will be good time when i can get 6ms latency and more apps develop for music. Looking forward to it :D

thanks again.

---

