---
title: "xbmc vs lightdm: slow interface or muted pulseaudio"
date: 2013-09-18
forum: Multimedia Software
---

### Post by pupizoid on 2013-09-18
Hi!
My problem is when I start xbmc directly from console I've got very slow interface and in power off menu I haven't options "shutdown" and "reset". In the other hand if I start xbmc throw lightdm interface and switching off is OK, but lightdm mutes pulseaudio (or alsa?) and I can't unmute it back from xbmc. Even if I logging into unity, unmute and go back to lightdm, after logging in xbmc I have muted soud card again. But if I logging into untiy, unmute soundcard, run mpd to play music, go back to lightdm then (miracle!) everything is ok and I have access to sound card for xbmc!
I use Ubuntu 12.04.3 Server with apache2, mpd, transmission-daemon and pulseaudio server (runs automatically on boot for accepting streams from laptop).
I've tried to set up channel levels in alsamixer and run alsactl store as root, but useless.
I've tried to run dbus and ck-launch-session before starting xbmc from console but useless.

I have 2 questions, any of it should solve my problem:
1) How to launch xbmc like lightdm it does but without one?
2) How to prevent lightdm mutes sound output?

Any thoughts and opinions are appreciated!!
Hopefully, Dennis.

---

