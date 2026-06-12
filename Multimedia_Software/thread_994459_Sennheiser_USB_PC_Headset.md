---
title: "Sennheiser USB PC Headset"
date: 2008-11-26
forum: Multimedia Software
---

### Post by katzian on 2008-11-26
Dear Ubuntu Forums haha:
I have a Sennheiser USB PC Headset. Actually my sound work isn't working as it should and this Headset brings a soundcard inside, so without using it, my sound experience goes way lower.
As I'm not a console fan but I have also tryed some things with it, I first went to System -> Preferences -> Sound (maybe it's different but I'm using Ubuntu in spanish language so I dunno :)).
There, I could find "Sennheiser Communications Sennheiser USB Headset USB Audio (ALSA)" listed. So I made all things to be reproduced by that soundcard and then I clicked "Test" (well here it says "Probar", that means "try" or "test" or "prove").
So I get this error message: ```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: No se pudo abrir el dispositivo de audio para reproducción.
```
"No se pudo abrir el dispositivo de audio para reproducción." means "The dispositive for audio playing couldn't be opened" or something like that.

Well I don't know what to do!

I googled if someone had experienced and solved before this same problem and I got to this topic: [http://ubuntuforums.org/showthread.php?t=382583](http://ubuntuforums.org/showthread.php?t=382583). No one answered him and it's archived also so... new topic here!

Actually if I connect this headphone without the USB integrated soundcard into the green-pink (audio-mic) jacks or how the hell are they called, sound works "perfectly". Well, it works as it shoulds so it sucks because it's too low and too bad, cos as I said before, my soundcard is malfunctioning.

If someone wants me to do some type of console-tests and paste the results or something I will make them for sure! I want to fix this cos it's really important for my Ubuntu experience

Thanks in advance and sorry for the large post (I'm expecting tl;dr =/)

Also: USB works, and same headset (using the USB integrated soundcard) works like a charm on Windows.

---

### Post by psyke83 on 2008-11-26
If you're on Hardy or Intrepid, you should configure your headset through PulseAudio instead of the Sound Preferences (which only controls GStreamer applications, by the way).

Follow [this]("http://ubuntuforums.org/showthread.php?t=789578") guide, and be sure to read it fully or else you won't see how to switch between playback and recording devices (either system-wide or per-application).

P.S. Helmi may have been suffering from a suboptimal PulseAudio configuration, though the post pre-dates Hardy. Nevertheless, keep in mind that Skype needs manual configuration to use PulseAudio correctly - it's explained in the guide.

---

### Post by katzian on 2008-11-26
> **psyke83 said:**
> If you're on Hardy or Intrepid, you should configure your headset through PulseAudio instead of the Sound Preferences (which only controls GStreamer applications, by the way).

Follow [this]("http://ubuntuforums.org/showthread.php?t=789578") guide, and be sure to read it fully or else you won't see how to switch between playback and recording devices (either system-wide or per-application).

P.S. Helmi may have been suffering from a suboptimal PulseAudio configuration, though the post pre-dates Hardy. Nevertheless, keep in mind that Skype needs manual configuration to use PulseAudio correctly - it's explained in the guide.

Works perfectly. Thank you so much =D. I tryed searching but I dunno I had to search about PulseAudio, I know that it ships with Ubuntu since 8.04 but I didn't knew about this things. I can hear my music better now, :lol:

---

