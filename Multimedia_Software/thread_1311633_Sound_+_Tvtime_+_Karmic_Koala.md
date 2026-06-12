---
title: "Sound + Tvtime + Karmic Koala"
date: 2009-11-02
forum: Multimedia Software
---

### Post by ppjose on 2009-11-02
Hi!

I only have sound on tvtime if I run the test in gstreamer-properties,

any solution?

thanks!!!

---

### Post by ppjose on 2009-11-03
up!

---

### Post by ppjose on 2009-11-04
any ideas?

thanks!

---

### Post by ivan.zivkovic on 2009-11-04
I am having also problem with Sound + TVTime + Karmic Koala

more info ... look like problem with device? wrong device ID?

ivanz@ivanz-desktop:~$ more /var/log/syslog |grep pulseaudio
Nov  4 18:30:14 ivanz-desktop pulseaudio[1657]: module-alsa-card.c: Failed to find a working profile.
Nov  4 18:30:14 ivanz-desktop pulseaudio[1657]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="1" card_name="alsa_card.1" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
...
Nov  4 19:57:08 ivanz-desktop pulseaudio[2714]: ratelimit.c: 9 events suppressed
...
Nov  4 20:45:52 ivanz-desktop pulseaudio[2714]: ratelimit.c: 247 events suppressed
Nov  4 20:45:56 ivanz-desktop pulseaudio[2714]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
Nov  4 20:45:56 ivanz-desktop pulseaudio[2714]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_via82xx'. Please report this issue to the ALSA developers.
Nov  4 20:45:56 ivanz-desktop pulseaudio[2714]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
Nov  4 20:45:58 ivanz-desktop pulseaudio[2714]: ratelimit.c: 55 events suppressed
...

ivanz@ivanz-desktop:~$ lspci
...
00:0c.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev f0)
...
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)


I have sound now!!! I have read the [http://ubuntuforums.org/showthread.php?p=8109989](http://ubuntuforums.org/showthread.php?p=8109989)

Comm. that helped me is

amixer -c 0 sset Aux,0 80%,80% unmute

---

