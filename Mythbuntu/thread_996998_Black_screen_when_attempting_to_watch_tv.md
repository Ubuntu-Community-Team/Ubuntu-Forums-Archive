---
title: "Black screen when attempting to watch tv"
date: 2008-11-29
forum: Mythbuntu
---

### Post by jonta on 2008-11-29
I've recently built a htpc-computer with a Hauppauge! WinTV-PVR-150MCE, PCI-card and installed mythbuntu 8.10 on it. My goal is to be able to watch and record tv but there are problems.

In the initial setup i have defined my wintv-card under capture cards, no problems.
I then add a video source, i choose the swedish one, it tells me i need to specify channels in the terminal so i switch to the terminal and select yes on the channels i know i have.
I then enter the Input Connections, choose my capture device, choose video sorce, the one i specified earlier.
I then choose scan for channels and it does so.
The channels it finds are "unknown 203" etc so i can't sort them as i don't know which is which but i exit the setup menu and then try to "Watch TV"
I only get a black screen, i cannot type or do anything, after a while i get back to the first "Watch TV" etc menu.
I have not enabled to use the wintv-cards tv-out to watch tv.

I'm not new to linux but i am new to PVR etc. What information do i get from the xmltv-source? Freqs of the channels or just whats on different channels?
And why is the screen only black when i try to watch tv?

I do get some errors in the errorlog:
2008-11-29 17:48:28.778 TVRec(1): Changing from None to WatchingLiveTV
2008-11-29 17:48:28.801 TVRec(1): HW Tuner: 1->1
2008-11-29 17:48:29.929 NVR(/dev/video0): Unknown video codec.  Please go into the TV Settings, Recording Profiles and setup the four 'Software Encoders' profiles.  Assuming RTjpeg for now.
2008-11-29 17:48:29.955 NVR(/dev/video0) Error: Unknown audio codec
2008-11-29 17:48:29.993 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
cannot open vbi device
2008-11-29 17:48:29.994 NVR(/dev/video0): Won't work with the streaming interface, falling back
2008-11-29 17:48:30.133 NVR(/dev/video0) Error: Can't open vbi device: '/dev/vbi'
VIDIOCGMBUF:: Invalid argument

Looks like it cannot open my tv-card, but i don't know why.

---

