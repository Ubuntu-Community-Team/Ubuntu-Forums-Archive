---
title: "No sound"
date: 2009-08-02
forum: Multimedia Software
---

### Post by farazhussain on 2009-08-02
Hello,

I have Ubuntu 9.04 on my school desktop running great. But there's no audio.  I have used Ubuntu on my laptop for many years and done many installations but never had this problem

I tried to fiddle with settings but am confused because there are too many "devices" inside volume control. Here's the list:


Intel ICH5 (alsa mixer)
Dell Sound Blaster Live (alsa mixer)
Analog Devices AD1980 (OSS mixer)
Playback Intel ICH5 - Intel ICH5 (PulsAudio Mixer)
Playback: Dell Sound Blaster Live! - EMU10K1X Fron (PulseAudio Mixer)
Capture: Monitor or Intel ICH5 - Intel ICH5 (PulseAudio Mixer)
Capture: Intel ICH5 - Intel ICH5 (PulseAudio Mixer)
Capture: Monitor of Dell Sound Blaster Live! - EMU10K1X Front (PulseAudio Mixer)
Capture: Dell Sound Blaster Live!- EMU10K1X Fron (PulseAudio Mixer)

I just want to be able to play mp3, etc and flash audio. 

Thanks in advance.

---

### Post by igorzwx on 2009-08-02
You can try to install another Ubuntu 9.04
in dual boot (for experiments).

You may try to make experiments with ALSA and esound, or else.
It might be reasonable to have several Ubuntu installed on the same box
(with different sound systems).

You may try OSS4, if your hardware is supported:
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

**Does OSS Support My Hardware?**

 Check the list [here]("http://mercurial.opensound.com/?file/6bf18b4a87d6/devlists/Linux"). Some devices may not have full functionality (e.g. the X-fi module is limited to stereo output at the time of this writing, and jack sensing may not work on Azalia-compliant "High-Definition" devices, which are very common on motherboards and laptops today). If you're in doubt, consult the "Additional Support" sources found towards the end of this document.

---

### Post by farazhussain on 2009-08-03
I got this working actually. I fiddled with alsamixer and say that it was using the dell card. So I switched to Dell in settings and it worked.

---

