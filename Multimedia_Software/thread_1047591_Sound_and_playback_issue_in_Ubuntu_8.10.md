---
title: "Sound and playback issue in Ubuntu 8.10"
date: 2009-01-22
forum: Multimedia Software
---

### Post by kerouacbuff on 2009-01-22
Hello everyone,

I posted a previous thread and did not get a response, but now I am not lazy, so I can explain my problem as detailed as possible. It all started on Monday night. I went to play a youtube video but there was no sound. I checked the sound card and it's detected; but when I go into Banshee there is no playback and it just says that it is idle. I don't think this has anything to do with my sound card because my sound card is already enabled. Are playback issues related to Gstreamer? I honestly don't remember what I did before for it to all of a sudden quit working. Is there a way to diagnose the problem? I already tried re-installing Gstreamer but that did not fix it. I have looked on countless websites trying to figure out how to solve the problem. I don't want to have to re-install Ubuntu, as that would be so much of a hassle as I have a lot of music on this computer. Please help me even if you troubleshoot. Thank you so much!

---

### Post by yt_l9 on 2009-01-22
Is your system using the right sound chip? I'd check your sound settings in >preferences>sound and make sure the right one is selected.

---

### Post by kerouacbuff on 2009-01-22
> **yt_l9 said:**
> Is your system using the right sound chip? I'd check your sound settings in >preferences>sound and make sure the right one is selected.

Now it is using the right sound chip but still no sound. Thank you for the reply! :)

---

### Post by markbuntu on 2009-01-22
Try changing system/preferences/sound to alsa or pulseaudio and set system/preferences/mutimedia system selector/audio (gstreamer control) to the same thing.

---

