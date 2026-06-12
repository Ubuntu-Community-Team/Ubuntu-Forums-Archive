---
title: "alsa / pulseaudio dummy output problem"
date: 2013-11-17
forum: Multimedia Software
---

### Post by progressnerd on 2013-11-17
Ever since upgrading from Precise to Raring and now Saucy, I get no audio on login. From suggested fixes around the web, I run these two commands to get my audio working again, everytime after logging in:
> 
  sudo killall pulseaudio
  sudo alsa force-reload


Can I avoid doing that?

My syslog has these juicy tidits:
> 
Nov 17 01:23:42 machinename pulseaudio[1482]: [pulseaudio] module-alsa-card.c: Failed to find a working profile.
Nov 17 01:23:42 machinename pulseaudio[1482]: [pulseaudio] module.c: Failed to load module "module-alsa-card" (argument: "device_id="1" name="usb-046d_081b_3F567BA0-02-U0x46d0x81b" card_name="alsa_card.usb-046d_081b_3F567BA0-02-U0x46d0x81b" namereg_fail=false tsched=yes fixed_latency_range=no ignore_dB=no deferred_volume=yes use_ucm=yes card_properties="module-udev-detect.discovered=1""): initialization failed.


I don't actually call my machine "machinename" ... just anonymized it :)

My alsa info before running the script:
[http://www.alsa-project.org/db/?f=3e5b3dc38871e524e1ec1bfd11a1ec1332355fc2](http://www.alsa-project.org/db/?f=3e5b3dc38871e524e1ec1bfd11a1ec1332355fc2)

My alsa info after running the script:
[http://www.alsa-project.org/db/?f=d9789e80b6cb060d9b3b65a651d26b90c8ec09d4](http://www.alsa-project.org/db/?f=d9789e80b6cb060d9b3b65a651d26b90c8ec09d4)

And the heres the diff of those two files. It includes some meaningless time/date differences, but including the full thing for completeness:

> 6c6
< !!Script ran on: Sun Nov 17 06:40:42 UTC 2013
---
> !!Script ran on: Sun Nov 17 06:46:05 UTC 2013
593d592
<   Device: name="HDMI 2", type="HDMI", device=8
689,691c688,690
< crw-rw----  1 root audio 116,  8 Nov 17 01:23 /dev/snd/pcmC0D0c
< crw-rw----  1 root audio 116,  7 Nov 17 01:23 /dev/snd/pcmC0D0p
< crw-rw----  1 root audio 116,  6 Nov 17 01:23 /dev/snd/pcmC0D1p
---
> crw-rw----  1 root audio 116,  8 Nov 17 01:45 /dev/snd/pcmC0D0c
> crw-rw----  1 root audio 116,  7 Nov 17 01:45 /dev/snd/pcmC0D0p
> crw-rw----  1 root audio 116,  6 Nov 17 01:45 /dev/snd/pcmC0D1p
693,697c692,696
< crw-rw----  1 root audio 116,  4 Nov 17 01:23 /dev/snd/pcmC0D3p
< crw-rw----  1 root audio 116,  3 Nov 17 01:23 /dev/snd/pcmC0D7p
< crw-rw----  1 root audio 116,  2 Nov 17 01:23 /dev/snd/pcmC0D8p
< crw-rw----  1 root audio 116, 12 Nov 17 01:23 /dev/snd/pcmC1D0c
< crw-rw----  1 root audio 116,  1 Nov 17 01:23 /dev/snd/seq
---
> crw-rw----  1 root audio 116,  4 Nov 17 01:45 /dev/snd/pcmC0D3p
> crw-rw----  1 root audio 116,  3 Nov 17 01:45 /dev/snd/pcmC0D7p
> crw-rw----  1 root audio 116,  2 Nov 17 01:45 /dev/snd/pcmC0D8p
> crw-rw----  1 root audio 116, 12 Nov 17 01:45 /dev/snd/pcmC1D0c
> crw-rw----  1 root audio 116,  1 Nov 17 01:45 /dev/snd/seq
733c732
<   Subdevices: 0/1
---
>   Subdevices: 1/1
1637c1636
< 			access 'read write locked'
---
> 			access 'read write'
1706,1707c1705,1706
< 		value.0 3
< 		value.1 4
---
> 		value.0 0
> 		value.1 0
1771a1771,1773
> snd_seq_midi
> snd_seq_midi_event
> snd_seq
1814,1815d1815
< snd_seq_midi
< snd_seq_midi_event
1817d1816
< snd_seq

Any help?

---

