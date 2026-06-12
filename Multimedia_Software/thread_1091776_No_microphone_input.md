---
title: "No microphone input"
date: 2009-03-09
forum: Multimedia Software
---

### Post by amrbekhit on 2009-03-09
Hello all,

I am unable to get any input from my microphone at all, although I have no problems listening to sound. In volume control, I checked the CAPTURE feedback tick box and set it to max and I can hear myself speak into the microphone but I cannot get applications like skype or sound recorder to get any input.

All the options in Sound Preferences are set to Autodetect, apart from sound capture, which is set to ALSA - I have tried all the other options and they are either the same, or they result in an error message when I try to test them and crash the sound preferences dialog.

I'm using ubuntu 8.10 and my sound card is a Sound Blaster Live! 24-bit, which is built into my MSI K8N SLI Platinum motherboard.

Here is the output from amixer:

```
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 65536
  Mono:
  Front Left: Playback 65536 [100%] [on]
  Front Right: Playback 65536 [100%] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 65536
  Front Left: Capture 65536 [100%] [on]
  Front Right: Capture 65536 [100%] [on]
```

--Amr

---

