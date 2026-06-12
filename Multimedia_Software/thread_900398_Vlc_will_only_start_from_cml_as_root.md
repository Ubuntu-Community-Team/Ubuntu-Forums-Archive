---
title: "Vlc will only start from cml as root"
date: 2008-08-25
forum: Multimedia Software
---

### Post by Blackcabs on 2008-08-25
Please can you help for some reason my vlc player will not open from the "Applications/Sound & Video/vlc menu although if i use sudo vlc from the cml it opens however i am bombarded with warnings that this is not safe and should not be done. I have just reinstalled vlc using a very good thread posted on this site [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) but its still the same. PS not sure if this is connected but after i installed vlc the very first time,, when i hovered the mouse pointer over a media file there was no sound,, when before there used to be.In order to get sound again i went to SYSTEM/Preferences/sound and had to change the AUTO DETECT setting to ALSA hope this all makes sense thanks Paul :confused:

This is the output that i get now when i try to run vlc as root

VLC media player 0.8.6e Janus
starting VLC root wrapper... using UID 1000 (paul)
libnotify-Message: Unable to get session bus: Failed to connect to socket /tmp/dbus-4WlGIrm9l0: Connection refused
[00000559] notify interface error: can't find notification daemon
[00000559] main interface error: no suitable interface module
[00000001] main private error: interface "notify,none" initialization failed

***************************************
* Running VLC as root is discouraged. *
***************************************

 It is potentially dangerous, and might not even work properly.

** (.:7612): CRITICAL **: gtk_pizza_set_size: assertion `pizza != NULL' failed
[00000357] access_http access: Raw-audio server found, mp3 demuxer selected
[00000392] pulse audio output error: Failed to connect to server: Connection refused
[00000392] pulse audio output error: Pulse initialization failed
[00000435] access_http access: Raw-audio server found, mp3 demuxer selected
[00000392] pulse audio output error: Failed to connect to server: Connection refused
[00000392] pulse audio output error: Pulse initialization failed

---

### Post by gandaran on 2008-08-25
yes, it's not safe to run vlc as root, if you change a setting at root level, that setting will also apply for user vlc and with different root settings you may not be able to remove vlc completely from you system later.
just find the hidden home vlc folder with the user configuration files, delete the folder and start vlc again, should work.

you may need to fix the sound problem.
I don't know exactly what you have installed by ubuntu-freak's thread, I have been reading it and there's a lot there I don't recommend installing unless you have some kind of problem (like alsa-oss).
if you want to install an application just open you synaptic package manager, look for the program, (like vlc) check-mark for install (or complete removal) and click the apply button

---

### Post by Blackcabs on 2008-08-25
Thankyou Grandaran i will delete that folder. what i was trying to explian about the sound was... You know when you place your mouse pointer over a media file "ie a Mp3" a small bubble appears with a musical note icon in the middle, and you then hear that particular tracks sound. well after vlc was installed those icon bubbles appeared but there was no sound. So i went to system/preferences/sound, and all the settings were set to AUTO DETECT . I had to change these to ALSA to get those bubbles to work again. So i questioned why after installing vlc why didn't they work anymore

Thanks again Paul

---

### Post by Blackcabs on 2008-08-25
[B]Thanks Grandaran ,Brilliant worked 100 % :popcorn:

---

