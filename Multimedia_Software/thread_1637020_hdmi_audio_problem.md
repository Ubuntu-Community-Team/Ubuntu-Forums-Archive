---
title: "hdmi audio problem"
date: 2010-12-03
forum: Multimedia Software
---

### Post by mwl128340 on 2010-12-03
hey all, 
ive recently encountered a sound issue and i was hoping someone much smarter than me can assist me. i recently installed the nvidia gt220 in my box and was thrilled at how well it worked with hdmi until i tried to use the audio. ive been scouring through threads for a few hours now and got somewhat working but not sure what to do now. i updated my alsa and went into the alsamixer and it does detect my gt220. i unmuted all spdif and tested the sound and with success the sound test works. i know the card and device numbers that work with the audio but now sure where to make changes so it will default to that device instead of the onboard audio that it seems to try to use now. im really new to linux so if im not good at explaining my situation, i apologize. thank you. ps. im running lucid 10.04

---

### Post by lidex on 2010-12-04
> **mwl128340 said:**
> hey all, 
ive recently encountered a sound issue and i was hoping someone much smarter than me can assist me. i recently installed the nvidia gt220 in my box and was thrilled at how well it worked with hdmi until i tried to use the audio. ive been scouring through threads for a few hours now and got somewhat working but not sure what to do now. i updated my alsa and went into the alsamixer and it does detect my gt220. i unmuted all spdif and tested the sound and with success the sound test works. i know the card and device numbers that work with the audio but now sure where to make changes so it will default to that device instead of the onboard audio that it seems to try to use now. im really new to linux so if im not good at explaining my situation, i apologize. thank you. ps. im running lucid 10.04

One of the best threads I've seen is here:
[http://ubuntuforums.org/showthread.php?t=1552250](http://ubuntuforums.org/showthread.php?t=1552250)
Maybe not the same hardware, but should get you on the right track.

---

### Post by frankcm3 on 2010-12-04
I had a similar problem with a small form home theater pc (Zotac Ion) where I am running 10.10 and XMBC. I had to check a couple of settings in the Alsa
In terminal type "alsamixer" if the hdmi appears there make sure that it is not muted.

If the hdmi does not appear there or has a value of "00" that cannot be changed follow the instructions for editing the alsa config file in the link below.  I only had to add 2 or three lines to the file.

If you have never altered these files before it easier than it looks. I am a new user and I used "vi" to edit the config file.


[http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240]("http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240")

---

### Post by mwl128340 on 2010-12-05
ok, thank you guys.  ill give it a try, and if i have to ill just use a different cable for audio, as cheesy as that is.thank you for the help tho.

---

### Post by mwl128340 on 2010-12-11
i ended up getting the sound to work. i used [http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/) for instructions to update alsa. im guessing i didnt install it correctlky the first time. thank you  for the help and hopefully this will help someone else.

---

