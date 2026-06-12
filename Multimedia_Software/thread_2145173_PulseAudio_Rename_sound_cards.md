---
title: "PulseAudio Rename sound cards"
date: 2013-05-14
forum: Multimedia Software
---

### Post by Martin02 on 2013-05-14
I am trying to make a couple of applications PulseAudio compatible, however the problem with PulseAudio is that whenever the applications are stopped or restarted, the revert back to the PulseAudio "default" sound card and not to the sound cards they need to be connected to. Very irritating.

```
$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfbbf8000 irq 46
 1 [U0xd8c0x0c     ]: USB-Audio - USB Device 0xd8c:0x0c
                      USB Device 0xd8c:0x0c at usb-0000:00:1d.0-1.3, full speed
 2 [Device         ]: USB-Audio - C-Media USB Audio Device
                      C-Media USB Audio Device at usb-0000:00:1d.0-1.6, full speed
 3 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xfbcbc000 irq 47
```

[LIST]
[*]"Device" is the USB sound card physically connected to my transceiver (HF radio).
[*]"U0xd8c0x0c" is the Cyber Acoustics USB headset is the device I want for the user to interact with the transciever.
[*]"Intel" and "Generic" are onboard sound cards for the PC.  I currently do not use Generic.
[/LIST]

PulseAudio and PulseAudio Volume Control are great, but in their default configuration, these do not lend themselves very well to pinning a sound card's channels to any specific application "only when" that app is running or asking for a sound card.

As best I can tell, PulseAudio only offers "default" option that these applications can connect to reliably which is usually the internal sound card or whatever I set as the fallback card.

It gets tricky here as "default" needs to remain the PC's internal sound card for every other application that may need to be running at the same time. :/

What would be really handy is for PulseAudio to expose the other 3 sound cards rather than letting ALSA expose them and perhaps renamed to something more meaningful and obvious what the device is.

ALSA's .asoundrc file might be the most appropriate solution and let PulseAudio exposed the new names, but it you don't write that file absolutely correctly, it will leave the entire system unstable and reporting errors to wherever Ubuntu Error Reporting sends them.  I had to delete the file and reboot to regain control.

I've considered and experimented with using pasuspender but why should I stop PulseAudio completely just because I want to use my radio?  This leaves all the other apps with nothing to connect to.

I need a way for PulseAudio to exposed the exact same names every single time to the applications that need a specific sound card.

Please don't respond with "Google .asoundrc" as this is a very dark and ugly road. BTDT.

Thank you for your time and expertise.

Luther

---

