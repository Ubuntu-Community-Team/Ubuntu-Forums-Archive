---
title: "Alsa - Terratec Aureon"
date: 2008-09-06
forum: Multimedia Software
---

### Post by bugg_tb on 2008-09-06
Hi Guys,

I've installed Hardy and I'm trying to get 5.1 output working with my Terratec Aureon Usb sound card, I've tried about a million different configurations, including:
[http://alsa.opensrc.org/index.php/Terratec_Aureon_5.1_USB_MK.2](http://alsa.opensrc.org/index.php/Terratec_Aureon_5.1_USB_MK.2)
and
[http://ubuntuforums.org/showthread.php?t=31829](http://ubuntuforums.org/showthread.php?t=31829)

but none work and I just get front left and front right when I do the speaker test.

What on earth could be wrong?

Cheers

Tom

---

### Post by haelen on 2008-09-15
I'm in the same position - except that I can't get it to work at all :(

Let me know if anyone gets back to you off forum. I'll subscribe to this thread.

Cheers,
Tim

---

### Post by Sevmpe on 2008-12-17
Hi,

Are you using PulseAudio? If so, you have to modify a configuration file to get surround sound. Instructions from the PulseAudio FAQ:

> Many people have a surround card, but have speakers for just two channels, so PulseAudio can't really default to a surround setup. To enable all the channels, edit /etc/pulse/daemon.conf: uncomment the default-sample-channels line (i.e. remove the semicolon from the beginning of the line) and set the value to 6 if you have a 5.1 setup, or 8 if you have 7.1 setup etc. After doing the edit, restart pulseaudio. 

Hope it helps.

---

