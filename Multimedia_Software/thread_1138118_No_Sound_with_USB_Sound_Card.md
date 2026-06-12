---
title: "No Sound with USB Sound Card"
date: 2009-04-26
forum: Multimedia Software
---

### Post by DualJazz on 2009-04-26
Hello everyone. I had a successful install of Ubuntu 9.04 and seems to be working fine. Previous network/internet problems were fixed. But I seem to be having problems with sound. I am currently using a Creative X-Fi Xmod sound card (USB). Under sound preferences:

Sound Playback (events) - Creative....Xmod USB Audio (OSS)
Sound Playback (movies) - Creative....Xmod USB Audio (OSS)
Sound Playback (audio conf.) - Creative....Xmod USB Audio (OSS)
Sound Capture (audio conf.) - Creative....Xmod USB Audio (OSS)
Default Mixer Track - Creative Xmod (ALSA)

The thing is, I cant get sound in games or even Ubuntu startup/event sounds. PidginIM plays message sounds, and Rhytmbox Music Player plays music. But their is no system sounds or game sounds! Please help!

Thank you for any replies :)

---

### Post by TMachado on 2009-05-13
Have same problem and no solution.

---

### Post by AudioPhlake on 2009-05-18
What worked for me was to add "Pulse Audio Volume Control" and "Pulse Audio Device Choser"  While I was playing music from Rhythmbox, I then went to "Pulse Audio Volume Control", "Playback", "Move Stream", select the usb device and YEAH!

---

### Post by TMachado on 2009-05-18
> **AudioPhlake said:**
> What worked for me was to add "Pulse Audio Volume Control" and "Pulse Audio Device Choser"  While I was playing music from Rhythmbox, I then went to "Pulse Audio Volume Control", "Playback", "Move Stream", select the usb device and YEAH!

But then, when you are not using Xmod, there's any output in your laptop speakers, or you have to change anything?

---

### Post by AudioPhlake on 2009-05-24
It appears to automatically go back to the internal when the USB is not attached.

---

### Post by TMachado on 2009-05-25
> **DualJazz said:**
> Hello everyone. I had a successful install of Ubuntu 9.04 and seems to be working fine. Previous network/internet problems were fixed. But I seem to be having problems with sound. I am currently using a Creative X-Fi Xmod sound card (USB). Under sound preferences:

Sound Playback (events) - Creative....Xmod USB Audio (OSS)
Sound Playback (movies) - Creative....Xmod USB Audio (OSS)
Sound Playback (audio conf.) - Creative....Xmod USB Audio (OSS)
Sound Capture (audio conf.) - Creative....Xmod USB Audio (OSS)
Default Mixer Track - Creative Xmod (ALSA)

The thing is, I cant get sound in games or even Ubuntu startup/event sounds. PidginIM plays message sounds, and Rhytmbox Music Player plays music. But their is no system sounds or game sounds! Please help!

Thank you for any replies :)

How do you get by "Default Mixer Track - Creative Xmod (ALSA)" ? I only have Creative Xmod Pulse Audio Mixer :(

With that option, I have the audio output very very low :(

---

