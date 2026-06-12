---
title: "mythbuntu --needs codecs?"
date: 2007-07-15
forum: Multimedia &amp; Video
---

### Post by kansei on 2007-07-15
I've been getting these messages in the log whenever I try to view livetv:

2007-07-15 02:52:50.283 TVRec(3): HW Tuner: 3->3
2007-07-15 02:52:50.728 Unknown video codec
2007-07-15 02:52:50.734 Please go into the TV Settings, Recording Profiles and
2007-07-15 02:52:50.735 setup the four 'Software Encoders' profiles.
2007-07-15 02:52:50.735 Assuming RTjpeg for now.
2007-07-15 02:52:50.736 NVR: Error, unknown audio codec
2007-07-15 02:52:50.754 NVR: Won't work with the streaming interface, falling back

Doesn't matter which tuner I use (it's a PVR-150 and a PVR-500, so all three tuners have the exact same config and settings and such) I get the same results. I went into synaptic and hunted down a few codecs and installed them, but it still seems broken.

And before anyone asks, yes, I'm well aware that mythbuntu is a very early alpha release but it holds a lot of promise so I want to use it even when it's this bleeding edge :)

Aside from not actually being able to watch TV and the bug where the install crashed on the last step (at this point the install is finished though, so it's no biggie), everything is working great and nicely integrated :)

it does suck that I have to log out to make any settings changes (well I am usually SSHd in so it's not that bad) because with fglrx and my video card (in windows or linux) whenever the driver is loaded it just sits at a black screen for 10-15 seconds. Constantly switching users is way slow.

---

### Post by kansei on 2007-07-15
Well I'm no longer getting the codec errors (went through every single transcoding profile and made sure it wasn't set to this mysterious RTjpeg business). I get this now:

2007-07-15 03:24:53.764 TVRec(3): Changing from None to WatchingLiveTV
2007-07-15 03:24:53.767 TVRec(3): HW Tuner: 3->3
2007-07-15 03:24:54.023 NVR: Won't work with the streaming interface, falling back
VIDIOCGMBUF:: Invalid argument

edit: wow I feel like a noob. I've been running a mythtv backend/frontend network for three years on Arch Linux and I guess the tuners must be set for V4L instead of mpeg2..

edit2: ok this is resolved now.. I'll edit the thread title to help future information seekers.

---

### Post by jdeslip on 2007-10-29
Hey, I had this problem you have.  The solution was to go back into mythtv-setup and change you capture card type to mpeg-2 under card caputure setup tab.  I had thought it recognized my card correctly, but it had not filled in all the right values.

---

