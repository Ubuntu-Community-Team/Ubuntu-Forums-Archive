---
title: "ALSA Terratec Aureon 7.1 Universe SPDIF no sound"
date: 2007-07-11
forum: Multimedia &amp; Video
---

### Post by comi on 2007-07-11
Hey there!

A simple description of my problem as until now no thread/howto/wiki page or anything could help me:
[LIST]
[*] HW: Terratec Aureon 7.1 Universe sound card
[*] Distro: Ubuntu 7.04 64-Bit
[*] Kernel: Linux nightfall-linux 2.6.20-16-generic #2 SMP Thu Jun 7 19:00:28 UTC 2007 x86_64 GNU/Linux[/LIST]First I was able to hear sound through SPDIF (coaxial cable connected to my receiver) in Gnome after fiddling with the Gnome-GUI-mixer and adding some .asoundrc I didn't know anything about.

Now after switching to the XFCE desktop environment, I'm not able to play any sound at all (Mplayer, Exaile, VLC, wine-based Games like WoW and so on). I know there might be some issues with OSS, but before - while using Gnome - everything worked (Sound in WoW through wine, Dolby Digital test samples, MP3s, movies and so on). In XFCE i enabled/disabled the "Launch Gnome services on startup" which doesn't help either. Well then I switched back to Gnome to see if it works there. Unfortunately not ;-)

Now to the steps I've done so far:
[LIST]
[*]  Checked cable connection ;-)
[*]  alsamixer (mute, sound levels)
[*]  Kernel modules
[*]  .asoundrc
[*]  Google[/LIST]After some research I collected all information I could get, please see [COLOR=Red]**[http://pastebin.com/f1149a88e](http://pastebin.com/f1149a88e)**[/COLOR] for a device listing, ALSA version, error messages and so on. The yellow marked lines should be the interesting ones or things I'm not sure if it's correct.

So I'd be very happy if somebody could give me a little hint. Thanks in advance and sorry for my bad English.

---

### Post by comi on 2007-07-12
Does anybody have an idea? I forgot to mention that the device is working in Windows, so a hardware defect is not possible.

---

### Post by comi on 2007-07-16
Sorry for bumping, but I'd like to resolve this issue, but don't know how. Any help appreciated.

---

### Post by fredj on 2007-07-16
The simple answer to your problems is reinstall Ubuntu with Gnome. If it works don't mess with it.

---

### Post by comi on 2007-07-17
Thanks for your reply!

Well sticking with Gnome isn't a real option for me, but I'll post again as soon as this issue is fixed.

---

