---
title: "HDMI Video after TV power off"
date: 2016-04-21
forum: Mythbuntu
---

### Post by mitchell2345 on 2016-04-21
Hi,

My frontend is running on a LIVA mini PC.  Since installing i have always had the issue where i loose video after powering my TV off and back on.  I hav this script installed to reset the output and it mostly works.

```
OUTPUT="HDMI1"
BAD_MODE="1280x720"
GOOD_MODE="1920x1080"

for MODE in $BAD_MODE $GOOD_MODE; do
 DISPLAY=:0 xrandr --output $OUTPUT --mode $MODE
 sleep 2
done
```

Recently i replaced my TV with a Panasonic Plasma and now after powering off TV i loose the video and the screen only fills about 25% of the screen.  The reset script doesnt help and my only solution is to reboot my frontend.

So...
Is there a way to force 1080p output no matter what is detected on the HDMI signal?  or a way to modify my scirpt to fix the small window issue?

details:
```
mitchell@liva:~$ mythfrontend --version
xprop:  unable to open display ''
Please attach all output as a file in bug reports.
MythTV Version : v0.27-193-g8ee257c
MythTV Branch : fixes/0.27
Network Protocol : 77
Library API : 0.27.20140323-1
QT Version : 4.8.6
Options compiled in:
 linux profile use_hidesyms using_alsa using_oss using_pulse using_pulseoutput using_backend using_bindings_perl using_bindings_python using_bindings_php using_crystalhd using_dvb using_firewire using_frontend using_hdhomerun using_ceton using_hdpvr using_ivtv using_joystick_menu using_libcrypto using_libdns_sd using_libfftw3 using_libxml2 using_lirc using_mheg using_opengl using_opengl_video using_qtwebkit using_qtscript using_qtdbus using_sdl using_taglib using_v4l2 using_x11 using_xrandr using_xv using_profiletype using_bindings_perl using_bindings_python using_bindings_php using_mythtranscode using_opengl using_vaapi using_vdpau using_ffmpeg_threads using_mheg using_libass using_libxml2
mitchell@liva:~$ 
mitchell@liva:~$ 
mitchell@liva:~$ uname -a
Linux liva 3.13.0-85-generic #129-Ubuntu SMP Thu Mar 17 20:50:15 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```
Thanks,
Mitchell

---

### Post by gottabefoss on 2016-04-21
Using XFce? This is a known bug with xfce-settings. ([https://bugs.launchpad.net/ubuntu/+source/xfce4-settings/+bug/1308105](https://bugs.launchpad.net/ubuntu/+source/xfce4-settings/+bug/1308105)). Try switching to KDE or Unity desktops and see if that fixes it.

---

