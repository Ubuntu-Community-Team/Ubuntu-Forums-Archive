---
title: "Firefox Audio - ALSA Error"
date: 2008-02-23
forum: Multimedia &amp; Video
---

### Post by ShawMishrak on 2008-02-23
I've been trying to get Flash installed in Firefox on Kubuntu 7.10 AMD64.  Installation went easily enough, but like many others it seems, I have no sound on flash sites.  The video is okay, just no sound.  None of the suggestions that I've found on this site seem to help.  I've tried installing the specialty packages, changing /etc/asound.conf, building the latest version of ALSA from source.

Sound seems to work in everything else (namely, Kaffeine and Amarok).  However, when I run firefox from the console, I get the following error when a flash movie with sound opens:

ALSA lib ../../../src/pcm/pcm.c:6617:(snd_pcm_slave_conf) unknown format unchanged

This error comes up at least 20 times a second and quickly floods the console window.

Any suggestions?

---

### Post by ShawMishrak on 2008-02-24
I solved the problem, after a few hours of fiddling this morning.  For those interested, it seems as though ALSA 1.0.16 has some issues that come up when using the Flash player plugin in Firefox on AMD64.  I'm not sure if it occurs on i386 or in other applications, but it was only a problem for me in Firefox.  The simple solution is to just revert back to ALSA 1.0.15.  I built alsa-driver, alsa-lib and alsa-utils 1.0.15 from source, and now sound is working in Flash!

---

