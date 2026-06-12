---
title: "Audacity or Ubuntu?"
date: 2007-10-04
forum: Multimedia &amp; Video
---

### Post by ghostofcain on 2007-10-04
Currently digitising my Vinyl collection using a **Numark TT usb turntable**, this works great, but Sound playback in **Audacity (1.3.3 beta)** is giving me headaches!

With the **input **set to **Usb audio codec** and **output** set to **alsa:via hw 0,0 or hw 0,1** I can record and get distorted playback via my speakers but it records at approx 33-50% realtime rate, although playback is very distorted whilst recording it plays in real time. The resulting sound file if played back is distorted and slowed also.

with **input** and **output** both set to **usb audio codec**, recording is in realtime but no sound issues from my system, although playback of the resulting file is fine, provided I set the playback device to **alsa:via hw 0,0**

I suspect this is a glitch with either my system settings? or the linux version of Audacity as the same set up works fine in Windoze XP, also using the beta of audacity

---

### Post by ghostofcain on 2007-10-04
anyone any ideas?

---

### Post by Jive Turkey on 2007-10-04
Audacity is a pretty heavy program for just playback and maybe even recording, I would use that more for post recording cleanup.  Try some of the other audio recorders, where possible select an uncompressed output format for the recording, then re encode to a compressed format.  

Another approach might be to set the thread priority of the recording program higher.  

Also, make sure your sample format isn't higher than you need, 44100Hz/24-bit max. Don't mess with Dithering either.

You might want to look for more info here as well, these guys are very hardcore:
[http://www.hydrogenaudio.org/forums/index.php]("http://www.hydrogenaudio.org/forums/index.php")

---

### Post by dinub1 on 2007-10-04
> **ghostofcain said:**
> Currently digitising my Vinyl collection using a **Numark TT usb turntable**, this works great, but Sound playback in **Audacity (1.3.3 beta)** is giving me headaches!

With the **input **set to **Usb audio codec** and **output** set to **alsa:via hw 0,0 or hw 0,1** I can record and get distorted playback via my speakers but it records at approx 33-50% realtime rate, although playback is very distorted whilst recording it plays in real time. The resulting sound file if played back is distorted and slowed also.

with **input** and **output** both set to **usb audio codec**, recording is in realtime but no sound issues from my system, although playback of the resulting file is fine, provided I set the playback device to **alsa:via hw 0,0**

I suspect this is a glitch with either my system settings? or the linux version of Audacity as the same set up works fine in Windoze XP, also using the beta of audacity

I have a similar USB turntable but made by ION. Its fairly simple, belt drive, but sounds is pretty good. I use to record with Audacity but under Windws XP. I may try installing Audacity ad try using it under Ubuntu.Never did it yet. Your settings are correct. The recording device should be the USB audio codec (provided with turntable) and the play back should be your sound card. If you play via the USB audio codec there will be no sound. Also enable "monitor input" during recording, so you can hear the turnable while recording thru your sound card. Otherwise it is mute. One thing I can think of... If I tried playing (Windows XP) any audio source with turnable connected to the USB port, the sound is muted! In order to restore normal sound via your sound card, you need to UNPLUG the turntable from the PC's USB port. This way the USB Audio connect will no loger be active and the sound will be played (normally) thru your sound card and driver. Normally when you plug the turnable inot the PC USB port, the USB Audio codec takes over and becomes your sound driver. This may be the source of your distortion. I sugest that you save the recording into a certain audio format, then try playing it after it is saved on HDD, but with turntable USB connector UNPLUGGED!
Let me know if this fixes your issue. There should be no distortion due to the fact that the USB signal is automatically monitored and kept under "normal" limits (below 0 dB). So the sound output shoud be clean. Mine is.

---

### Post by dinub1 on 2007-10-04
*[COLOR="Navy"]Also, make sure your sample format isn't higher than you need, 44100Hz/24-bit max. Don't mess with Dithering either.[/COLOR]*

I agree with you genenrally on your psot however sampling rate of 44 KHz.16 is enough for CD Audio reproduction and recording. 24 bit may be slightly better but not much. I also keep all the other settings unchanged. I get good results. But this has been all with Audacity under Windows XP.

---

### Post by ghostofcain on 2007-12-11
The only work around that seems to work, is to deselect the playthrough options, then it records fine but obviously I cant listen to it whilst recording

---

