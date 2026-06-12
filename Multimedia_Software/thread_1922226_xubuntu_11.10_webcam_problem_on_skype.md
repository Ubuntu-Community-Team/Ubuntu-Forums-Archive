---
title: "xubuntu 11.10 webcam problem on skype"
date: 2012-02-08
forum: Multimedia Software
---

### Post by kimberley on 2012-02-08
I have a Quickcam Messenger and cannot get a test picture on skype, however, there is a good pic on Cheese. Previously I had no problems on Ubuntu 10.4.

I have tried some terminal suggestions from the forum but none seem to work. I am a 'newbie' so am apprehensive about trying too many things without knowing the consequences. 

Can someone please help.
:KS

---

### Post by kimberley on 2012-02-11
> **kimberley said:**
> I have a Quickcam Messenger and cannot get a test picture on skype, however, there is a good pic on Cheese. Previously I had no problems on Ubuntu 10.4.

I have tried some terminal suggestions from the forum but none seem to work. I am a 'newbie' so am apprehensive about trying too many things without knowing the consequences. 

Can someone please help.
:KS
The Mutimedia system selector shows Default : 
Output: Plugin - Auto detect, Device: unsupported 

Input: video for Linuxx2(v412)
USB camera (046d:08da)

My camera is therefore being detected but is shown as unsupported, although it works perfectly in Cheese. Does anyone know why this is and is there a solution?

Looking forward to hearing from someone please.

---

### Post by kimberley on 2012-02-20
In trying to solve my webcam problem on skype I downloaded guvcview and have a good webcam picture and also on Cheese but now have the following terminal message.  Have I confused the issue by doing this as I now have the following terminal message:

flower@flower:~$ vlc v4l2:///dev/video0
VLC media player 1.1.12 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x8e97b34] main interface error: no suitable interface module
[0x8df6914] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x8df6914] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x8e9520c] [rc] lua interface: Listening on host "*console".
VLC media player 1.1.12 The Luggage
Remote control interface initialized. Type `help' for help.
> [0x8ea830c] main decoder error: no suitable decoder module for fourcc `MJPG'. VLC probably does not support this sound or video format.
[0x8ea830c] main decoder error: No suitable decoder module
[0x8ea830c] main decoder error: VLC does not support the audio or video format "MJPG". Unfortunately there is no way for you to fix this.

If there is any bright person out there who knows a way around this problem I will be forever in their debt!:popcorn:

---

### Post by kimberley on 2012-07-08
Solved my problem by uninstalling Skype beta version 2.1 and installing latest version 4.0 which works perfectly - video and audio without any adjustment.

---

