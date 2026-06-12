---
title: "Asus vivobook S400CA- ubuntu 13.10 mic not working."
date: 2013-11-04
forum: Multimedia Software
---

### Post by lvgandhi on 2013-11-04
I am dual booting ubuntu 13.10 with windows 8.1. Mic works ok in windows. It is not working in ubuntu.
lspci shows
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
	Subsystem: ASUSTeK Computer Inc. Device 10fd
	Flags: bus master, fast devsel, latency 0, IRQ 46
	Memory at f7e18000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
I have gone through various solutions like unlocking stereo and making volume 0 to one channel; trying dkms pkgs
and
echo "autospawn = no" > ~/.pulse/client.conf
 killall pulseaudio
oem-audio dkms pks not getting installed.
Other solutions also did not work.
Please suggest any solutions?

---

### Post by paavan.buddhdev on 2013-11-07
Heyo.

I've had a similar problem on the same laptop (but running 12.04) - and managed to solve it with this workaround [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/946232/comments/32](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/946232/comments/32).

> [COLOR=#333333][FONT=Ubuntu Mono]For those of you who are missing an internal mic port, edit /usr/share/[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]pulseaudio/[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]alsa-mixer/[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]paths/analog-[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]input-internal-[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]mic.conf[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono] and comment out all lines that start with "required-any".[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]It is important that you comment out (or remove) all those lines, if you leave one behind, it won't work.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]After the change, you can either execute "pulseaudio -k" or reboot for the changes to take effect.[/FONT][/COLOR]

Hope this helps.

Paavan

---

### Post by lvgandhi on 2013-11-09
After doing this Audacity which was recording, is not recording.

---

