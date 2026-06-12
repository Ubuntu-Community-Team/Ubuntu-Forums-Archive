---
title: "mythbuntu-repos not fetching 0.23"
date: 2010-05-26
forum: Mythbuntu
---

### Post by eppo on 2010-05-26
its been a while since i've updated mythtv, because it was just working.
since the tv season is over, i figured i would upgrade.
i have mythbuntu-repos installed, so i just did an apt-get update|apt-get upgdate
when i do mythfrontend --version i get this:
Please include all output in bug reports.
MythTV Version   : 0.22
MythTV Branch    : tags/release-0-22
Network Protocol : 50
Library API      : 0.22.20091023-1
QT Version       : 4.5.0
Options compiled in:
 linux release using_oss using_alsa using_pulse using_backend using_dvb using_frontend using_hdhomerun using_hdpvr using_iptv using_ivtv using_joystick_menu using_lirc using_mheg using_opengl_video using_opengl_vsync using_qtwebkit using_v4l using_x11 using_xrandr using_xv using_bindings_perl using_bindings_python using_opengl using_ffmpeg_threads using_live using_mheg

shouldnt i be seeing 0.23 as my version?
when i saw that i did:
dpkg-reconfigure mythbuntu-repos
it only gives me the option of 0.21 and 0.22
what do i need to do to get 0.23 as an option?

---

### Post by masux594 on 2010-05-26
What is your OS release version? is 10.04 or before? anyway, "apt" doesen't uninstall a software by itself.. So, if u have the 0.23 installed before, you still have it..

Sysc, A

---

### Post by eppo on 2010-05-26
actually, here is the myth version i'm running:
MythTV Version   : 23766
MythTV Branch    : branches/release-0-22-fixes
Network Protocol : 50
Library API      : 0.22.20091023-1
QT Version       : 4.5.0
Options compiled in:
 linux release using_oss using_alsa using_backend using_dvb using_frontend using_hdhomerun using_hdpvr using_iptv using_ivtv using_joystick_menu using_lirc using_mheg using_opengl_video using_opengl_vsync using_qtwebkit using_v4l using_x11 using_xrandr using_xv using_xvmc using_xvmc_vld using_xvmcw using_bindings_perl using_bindings_python using_opengl using_ffmpeg_threads using_live using_mheg

i'm looking to have it fetch 0.23, is that possible?
i'm running jaunty btw.

---

### Post by LowSky on 2010-05-26
take a look at this
[http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)

You really should upgrade to Ubuntu 10.04 for longer support

---

### Post by tgm4883 on 2010-05-26
Each release only supports 2 versions, basically what it shipped with and what it shipped with +1. IIRC, Jaunty shipped with 0.21, so you will only be able to choose from 0.21 and 0.22. To get 0.23, you would need to upgrade to Karmic minimum.

---

### Post by eppo on 2010-05-26
when i upgraded to jaunty i had issues with my raid not being recognized. i really dont want to go through that mess again. 
maybe one day if i can back up everything i have on it.

---

