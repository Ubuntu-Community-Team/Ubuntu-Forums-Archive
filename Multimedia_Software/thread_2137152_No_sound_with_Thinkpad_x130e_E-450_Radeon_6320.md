---
title: "No sound with Thinkpad x130e E-450 Radeon 6320"
date: 2013-04-19
forum: Multimedia Software
---

### Post by flammenwurfer on 2013-04-19
I'm not getting any audio on my Lenovo Thinkpad x130e.  I'm using the open source driver, not the proprietary one.  Running lubuntu 12.10.

When I run alsamixer it initially shows "HD-Audio Generic" and only lists S/PDIF.  If I hit F6 and select "HDA ATI SB" I have a lot more, such as Master, Headphone, Speaker, Mic etc...  Nothing is muted and the levels are all turned up, but I get no sound.

I have searched for solutions and found a suggestion to add "radeon.audio=1" to grub, but no luck. 

I just found another suggestion to install pulseaudio and pavucontrol, and that gets the sound working. 

Any ideas why alsa isn't working but pulse is?

---

