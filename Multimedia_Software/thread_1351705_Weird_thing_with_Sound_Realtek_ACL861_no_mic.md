---
title: "Weird thing with Sound Realtek ACL861 no mic"
date: 2009-12-10
forum: Multimedia Software
---

### Post by cladelpino on 2009-12-10
Hi! I've solved an issue in quite an unexpected way. And I would love to know what was the issue. :o

I own an Intel D101ggc motherboard, with the integrated soundcard aforementioned: Realtek acl861. I had to voice-chat the other day, and plugged a common mic. nothing. after a lot of checking, reading around, and all, I thought this was just a bug to be solved in future versions of either alsa, or ubuntu. At that time (and now) when I run alsamixer from terminal, it just doesn't show any "capture" devices: it appears as my soundcard didn't have any possibility for inputs. I tried every workaround and adding of magical lines to alsa-base , to no end.

Comes a day, when checking Synaptic, I see this "gnome alsa mixer", which appears to just provide a GUI for the said command. I run it. See a "Mic" , it's muted: turn it up, and I can suddenly hear myself typing !!!!! the mic now works!!!!. I run alsamixer again from term, just to check, and still, no capture devices. Ain't this strange ? Any idea as to which could be the "issue" ? I'm really happy now but since I'm a bit of a newbie to the linux enviroment, want to better understand what happened.

Any help or comments is appreciated. Was it magic ? :P

regards,
Claudio.

PD: just to add, when I run alsamixer from term now, the supposed "playback device" "Mic" is set at 0 vol... but i still can hear the mic.

---

