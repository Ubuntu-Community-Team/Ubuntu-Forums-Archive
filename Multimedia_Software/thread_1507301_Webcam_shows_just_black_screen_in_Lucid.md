---
title: "Webcam shows just black screen in Lucid"
date: 2010-06-11
forum: Multimedia Software
---

### Post by ftmichael on 2010-06-11
I have a Logitech Quickcam Chat webcam (USB ID **046d:092c**) that's worked with my Ubuntu with minimal problems (just some nVidia driver crap) for ages now.  I'm not using nVidia anymore (Intel now), but since my fresh install of Lucid, my webcam doesn't seem to capture anything.  It is detected by **lsusb**, but when I open Cheese, the picture is just black.  Skype doesn't give me any video at all, not even that annoying static or green lines.  Clicking the Test button in my Skype Options under Video doesn't do anything; double-clicking it gives me a full-screen grey screen - pressing Escape takes me back to the preferences window.  After I get the grey full screen and press Escape, the Test button is gone until I close the Options window and open it up again.

Going into **gstreamer-properties** and testing v4l2 (under Video -> Default Input) just shows me the 'Testing ... Click Ok to finish' window for ages until I close it -  no video appears or anything and I'm not entirely sure what I'm supposed to be seeing.  Testing with the 'Test Input' option does give me the coloured lines and static.  Testing v4l seems to make it crash, but no error comes up in the terminal I'm running it from.

**lsusb** output:

```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:092c Logitech, Inc. QuickCam Chat
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

When I run **gstreamer-plugins** from the terminal, as it starts I get this output:

```
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
```

Any thoughts?  Is the problem one or more of those missing plugins?

Thanks in advance!

---

### Post by no2498 on 2010-06-11
open cheese and set the pic size smaller should help you


hope this helps

---

### Post by ftmichael on 2010-06-11
Tried that ... no change, unfortunately.

---

### Post by no2498 on 2010-06-13
that is the norm for gstreamer-properties
do you have gstreamer,  good   bad and ugly   installed

you did not say if it did show in gstreamer-properties
did you try the bottom test button for each 1


open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1


hope this helps

---

### Post by ftmichael on 2010-06-13
I do have good, bad, and ugly installed.

Going into **gstreamer-properties** and testing v4l2 (using the bottom test button, which is for input) just shows me the 'Testing ... Click Ok to finish' window for ages until I close it - no video appears or anything and I'm not entirely sure what I'm supposed to be seeing. Testing with the 'Test Input' option does give me the coloured lines and static. Testing v4l seems to make it crash, but no error comes up in the terminal I'm running it from.  It just freezes and doesn't respond and I have to force-quit.

---

### Post by no2498 on 2010-06-13
make a new ? as you need a driver
un less gstreamer 10 is not loaded on your install
sorry i cant help any more than this

---

### Post by ftmichael on 2010-06-13
I'm pretty sure I have the correct driver (gspca, which [replaced spca5xx](https://help.ubuntu.com/community/Spca5xx) as of the Gutsy release).  **lsmod | grep gspca** gives me this output:

```
gspca_spca561           8415  0 
gspca_main             21199  1 gspca_spca561
videodev               34361  1 gspca_main
```

---

### Post by dbloom on 2010-06-13
i had a similar problem with a logitec webcam that i knew should work.  all i got was a black image, but the webcam was recognized.  i noticed that when i was messing with the sound and could tell that it was sourcing the webcam as the microphone.  

this may sound too simple, but unplugging it from the USB and plugging it back it fixed it.  i mention this because its not something i would have ever thought to try (ordinarily) and not sure why i did, but it did work.  

good luck!

---

### Post by ftmichael on 2010-06-13
Just tried, but unfortunately it didn't work.  That would have been amazing though.  Unless rebooting or restarting X or something might also help?

---

### Post by no2498 on 2010-06-14
just seen this it may help you

open a terminal type,  mplayer tv://


he said your webcam should come on in mplayer

hope it helps you

---

### Post by ftmichael on 2010-06-14
Webcam didn't open when I ran **mplayer tv://** in terminal, but that's probably good because it gave me a bunch of output:

```
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing tv://.
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
v4l2: your device driver does not support VIDIOC_G_STD ioctl, VIDIOC_G_PARM was used instead.
Selected device: Camera
 Capabilites:  video capture  read/write  streaming
 supported norms:
 inputs: 0 = spca561;
 Current input: 0
 Current format: unknown (0x31363553)
tv.c: norm_from_string(pal): Bogus norm parameter, setting default.
v4l2: ioctl enum norm failed: Invalid argument
Error: Cannot set norm!
Selected input hasn't got a tuner!
v4l2: Cannot get fps
v4l2: ioctl set mute failed: Invalid argument
v4l2: ioctl query control failed: Invalid argument
v4l2: ioctl query control failed: Invalid argument
v4l2: ioctl query control failed: Invalid argument
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Cannot find codec matching selected -vo and video format 0x31363553.
Read DOCS/HTML/en/codecs.html!
==========================================================================

v4l2: ioctl set mute failed: Invalid argument
v4l2: 0 frames successfully processed, 0 frames dropped.

Exiting... (End of file)
```

---

### Post by no2498 on 2010-06-14
we had to try it
i got the same as you on 2 computers 1 804 1 910
and booth my cams work


have i had you get this program yet wxcam

i find this 1 to work if cheese does not

read and install all the page tells you to

[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)


or try xawtv

---

### Post by ftmichael on 2010-06-14
I tried **xawtv** and it didn't work.  I just installed **wxcam** and opened it, and got this error:

```
An error has occurred during frame capture.
Please check the "frame format" options in the preferences menu.
```

I had a look, but I'm not sure what I should reset it to.  Its default setting is 'Auto' which you'd think would work! :P  I tried all of them; some gave me the same error, while others tried to show me a picture but just gave me lots of green noise.  I downsized the image from 352x288 to 176x144 and now I see myself (only with some 'frame format' settings, most notably YUV420P - other 'frame format' settings still give me that error), but with weird colours  - the top half of the image is yellow and the bottom half is pink, but about once a second it flashes so that the top half is blue and the bottom half is green - and there's a bunch of noise all over it as well.  Sizing it down more, to 88x72, just turns it into pink static with no flashing or anything, just what seems to be a still image of pink static.

When I start **wxcam** in terminal with YUV420P as the frame format, I get this output:

```
Determining video4linux API version...
Using video4linux 2 API
VIDIOC_ENUM_FRAMESIZES: Invalid argument
V4L2_CID_BRIGHTNESS is not supported
V4L2_CID_CONTRAST is not supported
V4L2_CID_GAMMA is not supported
V4L2_CID_SATURATION is not supported
Using V4L2_PIX_FMT_YUV420 pixel format
```

What's the 'VIDIOC_ENUM_FRAMESIZES: Invalid argument' about?  And why are those other settings not supported?  Is any of that part of my problem with Cheese and Skype?

---

### Post by ftmichael on 2010-06-14
Okay, I just opened Cheese again, and I have picture now.  I have no clue what changed.  I uninstalled **wxcam** to see if Cheese would still work, and it did.

Skype was fixed by changing the menu command from **skype** to **bash -c 'export LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so; skype'** as recommended elsewhere.  That didn't help anything before, but now that Cheese seems happy with the webcam, Skype's willing to work as well.

I'd still like to know what the problem was so I can fix it if it happens again, or if anyone else has the same problem.  Therefore I'm hesitant to mark this thread [SOLVED].

---

### Post by jmore9 on 2010-06-14
You could try using the following , except replacing camstream with your app.

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so camstream

I use a creative instant web cam that only uses the v4l-1 not -2

Hope that helps

---

### Post by no2498 on 2010-06-15
cheese has a good help file look in its faq's


its a shame wxcam does not work for you 
i can click it open and record in 5 sec

you should get it back and play with it a lot

have only seen 1 say they got the mic to work with cheese


but all in all glad you got it working

edit your first post to read solved

---

### Post by anto27373 on 2010-06-26
EDIT: when I mention Movie Player below I mean Totem (did not realise it was Totem until I looked in help)

I have a similar problem with Cheese and Skype. 

The webcam is working (can take photos & record video in Cheese).
And soon as I play back the recorded Video (with Movie Player) Cheese will display a picture!

Have not tested Skype with anyone yet. Just the blank screen in Options>Video>Test.

BUT this all resolves itself as soon as I run Movie Player.

Had the same problem with VLC (sound but no picture).
Changing the output options fixed this for VLC tho.
In Vlc Preferences> video> output > "x11 video output" 

any thoughts ?
could always just set Movie Player to run on startup I guess...

---

### Post by carniola on 2010-11-07
> Skype was fixed by changing the menu command from skype to bash -c 'export LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so; skype' as recommended elsewhere. That didn't help anything before, but now that Cheese seems happy with the webcam, Skype's willing to work as well.

This solved it for me as well. Thanks.

---

