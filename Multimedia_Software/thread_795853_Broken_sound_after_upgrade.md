---
title: "Broken sound after upgrade"
date: 2008-05-15
forum: Multimedia Software
---

### Post by rustysail on 2008-05-15
Hello.

I upgraded to Hardy, and my audio started acting very funny.  I turned on rhythmbox and it works fine.  However, when I go on youtube or any other flash site, the audio will not play.  At first I thought something was wrong with my flash player.  However, today, I turned on my computer and played an online video.  Once I turned on rhythmbox, it would not play music.  

It seems that only one will work per session.  Does anyone know how to fix this?  If so, I would appreciate your help very much.

Rusty

---

### Post by ubuntu-freak on 2008-05-15
> **rustysail said:**
> Hello.

I upgraded to Hardy, and my audio started acting very funny.  I turned on rhythmbox and it works fine.  However, when I go on youtube or any other flash site, the audio will not play.  At first I thought something was wrong with my flash player.  However, today, I turned on my computer and played an online video.  Once I turned on rhythmbox, it would not play music.  

It seems that only one will work per session.  Does anyone know how to fix this?  If so, I would appreciate your help very much.

Rusty

 
Hardy uses a new sound server, called PulseAudio. Gutsy used the ALSA sound server. You can go back to using ALSA by navigating to System > Preferences > Sound, and change it to ALSA, instead of Auto Detect. Also, just explicitly selecting PulseAudio has helped some users, rather than leaving it on Auto Detect. May be worth rebooting when testing each option, don't give up too quick. You will have to tell non-GNOME apps (VLC, MPlayer etc) if you decide to use ALSA in Hardy, which you can do in their preferences.
 
Nathan

---

### Post by thedarky on 2008-05-16
Coming up for air after a bit of a search through the threads, I've solved my particular problem - caused by the recent updates to the x server - by disabling the load of Pulse Audio X11 Session Management at startup altogether.

Although I found that reconfiguring the sound source pref to either ALSA or OSS gave me back the playback functionality, I couldn't recover the all-important FN tones (such as those indicating on/off for the trackpad - a must for a touch-typist) Plus booting was taking an extra age while Bluetooth, which I don't want, was getting assigned.

Without the Pulse Audio X11 Session Management gizmo loaded, I have the FN sounds back, and all other playback as desired.

You can change loading of stuff at startup in the System/Prefs/Sessions>Startup Programs tab.

---

