---
title: "Recordings that won't end"
date: 2013-04-03
forum: Mythbuntu
---

### Post by johnlatz on 2013-04-03
I recently re-installed Mythbuntu 12.04.2 LTS, set it up to grab repos (to get 0.26), and moved my databases and recordings over.  I've been chasing down some bugs and squashing them here and there, slowly, but there's one I can't get my head around.  I have two capture cards:  one HVR-1600 (on which the coax connector is mechanically broken, rendering the card analog only), the second an HVR-2250.  I can record fine on the HVR-1600 (analog), I can record fine on one half of the HVR-2250 (both analog and digital); the second half of the HVR-2250 analog works, digital has been having trouble.  

For a couple of weeks, I couldn't get the second half (digital) to record anything - I would get "zero length recordings".  Suspecting my cable company's signal quality, I've bumped up the time to tune, the time to lock signal, nothing worked until I installed an in-line amp, and now it can tune, lock, and record.  Problem is it won't stop recording.

Behold (note current time, note time recording started, note time recording was supposed to endure):
[IMG]http://latz-torres.hobby-site.org/Downloads/ScreenShot.png[/IMG]

The only way I can seemingly quit the recording is to restart mythtv-backend.  And if I don't catch it and restart, any additional recordings scheduled for that card fail as well.  Any ideas?



```
Please attach all output as a file in bug reports.MythTV Version : v0.26.0-138-g69cd78b
MythTV Branch : fixes/0.26
Network Protocol : 75
Library API : 0.26.20130225-1
QT Version : 4.8.1
Options compiled in:
 linux profile use_hidesyms using_alsa using_oss using_pulse using_pulseoutput using_backend using_bindings_perl using_bindings_python using_bindings_php using_crystalhd using_dvb using_firewire using_frontend using_hdhomerun using_ceton using_hdpvr using_iptv using_ivtv using_joystick_menu using_libcec using_libcrypto using_libdns_sd using_libxml2 using_lirc using_mheg using_opengl_video using_qtwebkit using_qtscript using_qtdbus using_v4l2 using_x11 using_xrandr using_xv using_bindings_perl using_bindings_python using_bindings_php using_mythtranscode using_opengl using_vaapi using_vdpau using_ffmpeg_threads using_live using_mheg using_libass using_libxml2

```

---

### Post by drewdin on 2013-04-04
I have this same issue, i have to restart to get it going and it happens at random. I'm looking forward to some answers!

---

### Post by TheFuzz4 on 2013-04-04
I had this issue as well when I was running 25 and only using the HVR 2250.  My problem was that tuners were in use by LiveTV and then the recording went to start and it couldn't because of the LiveTV (even if the user said yes to the recording on the screen).  I then upgraded to 26 and also put in a idle timeout on the LiveTV in case the TV got shut off without exiting the LiveTV.  I think that the other thing that fixed it for me was getting a HD HR Prime w/CableCard.  Now I have 5 tuners and I haven't had an issue ever since.

---

