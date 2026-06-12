---
title: "Issues with ATI 4850 and drivers"
date: 2008-07-30
forum: Multimedia Software
---

### Post by Enigmatic on 2008-07-30
I'm not sure if it's my drivers, but I've been having a number of issues that I did not see with my Nvidia card. It was running 8.04 as well, currently am on a fresh install of 8.04.

I realize these are not necessarily all related to video drivers, but if someone could steer me in the right direction that would be great.

Issues include:

-the odd crash of Firefox, not sure if it's Flash related. It just closes immediately

-stuttery video playback. I notice this only on (HD) wmv files. Not sure if this is related to the new GPU generation doing more video processing (CPU loads are surprisingly low with HD, granted I did upgrade my CPU)

-the odd X crash when playing videos. This seems to have improved a lot after installing more gstreamer plugins (I think).

---

### Post by grigio on 2008-07-31
Try with different kernels or video drivers and report bugs.

---

### Post by markbuntu on 2008-07-31
The firefox crashes could be related to flash, also, if you installed 8.04 you should have gotten about 286 updates, one of which includes and updated firefox 3.0 which is far more stable than the 3b5 in the release. If you installed 8.04.1 you should have this updated firefox already and the most likely cause of the crashes in that case would be flash 9, which does that. If you have installed 8.04 then run Update Manager to get all the updates, they fix many many problems.

I assume you are using the ati restricted driver fglrx for your 4850. If you do not have it, get the amdcccle, Catalyst Control Center from the repository with synaptic. You can find the Catalyst Control Center in Applications/Other, which may be hidden and can be unhidden in System/Preferences/Main Menu.

The Catalyst Control Center will allow you to make some adjustments in the 3D section that can help with playback issues. It is also a good idea with this driver to set Desktop Visual Effects to none when playing back video. You can also check in the information section to see which driver you are using, it should be 8.50.1 (8.6) or 8.51.3 (8.7)

If you are trying to play streaming HD video, your cpu may not be able to keep up with the download and playing at the same time or your connection may be too slow.

You can also try playing around with the video output driver in the applications preferences section but be prepared for crashes if you choose one that the driver does not like. gstreamer seems to work better than xine for many with your driver/card.

---

### Post by Enigmatic on 2008-08-09
It appears that Firefox crashing is due to Flash, but it's not too common.

The other crashes appear to be related to video/audio, and perhaps Totem. Hard to say for sure, because I've had it happen when opening mkv files in Totem, avi files as well as some streaming files in Firefox. Maybe I should try VLC for a while to see if it makes any difference.

Yes, I am on 8.04.1, all up to date. I am pretty sure I am on fglrx, as I have the Catalyst Control Center. I don't see anything in the 3D section that seems output related.

I have not been using Desktop effects and still get crashes. It appears that I am using gstreamer plugins and not xine.

---

### Post by Yellow Pasque on 2008-08-09
Your best bet is probably to wait for the radeonHD driver to develop. Basic mode-setting for R600/R700 is in place, but 2D/3D acceleration is being worked on at the moment.

---

### Post by markbuntu on 2008-08-11
You need to install libflashsupport for flash9 to stop crashing your system. Those crashes are caused by pulseaudio, not the video driver. If you want to see it happen for your self, Open the Pulse Audio Volume Control if you have it and play a flash video. You will see flash open and close streams in a blur until pulse crashes or locks up your system. Pulse can only play about 1,000 streams until it crashes, a limit the pulse devs thought could never be reached in normal use.

Anyway, lots of other people repot no problems at all with their 4850s. What does the information screen in the Catalyst Control Center tell you about the version it is running?

---

### Post by Enigmatic on 2008-08-11
I have libflashsupport installed. Crashes are not too frequent with Flash. I have moved to using VLC for video files, have not gotten a single crash yet (fingers crossed). Perhaps the codecs that Totem uses?

---

