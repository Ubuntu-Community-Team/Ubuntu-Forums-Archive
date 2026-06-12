---
title: "Web cam is upside down"
date: 2013-01-03
forum: Multimedia Software
---

### Post by rooney09 on 2013-01-03
Hi guys,
I've been looking for couple of days to fix my camera problem on skype (which is upside down) but still I haven't found any solution. I found the ajos's thread about fixing the camera but didn't work for me either..(probably cause I am a beginner and a noob in ubuntu)
As I remember I had the same problem on my Windows 7 and fixed it by a program called: Driver Genius Professional.
Well, I have Ubuntu 12.10 now.
My laptop is Asus K50IJ.

When I type ```
lsusb
```:
I get this:

> Bus 001 Device 002: ID 04f2:b071 Chicony Electronics Co., Ltd 2.0M UVC Webcam / CNF7129
Bus 006 Device 002: ID 046d:c019 Logitech, Inc. Optical Tilt Wheel Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I think this is the whole info I can give you for now :S
Any tips to fix it up will be greatly appreciated.
Thank you!

---

### Post by rooney09 on 2013-01-03
I am attaching a screen-shot.
[Here you go!](http://img802.imageshack.us/img802/9430/screenshotfrom201301031.png)

---

### Post by tgalati4 on 2013-01-03
It certainly gives your video conferences a sense of sophistication.

I would run with it.  Put your hands up in the air and pretend to be doing a hand stand.  Not many folks can do a video conference while doing a hand stand.

A quick search of the forum showed going back to 12.04 fixed the issue.  Not really a helpful fix.  Try posting a bug report.  There might be a work around using ffmpeg and /dev/video0, but a better fix would be to fix the webcam driver.

Perhaps there is a switch for the webcam module.  What module is being loaded for the webcam?

```
lsmod
```

Search "Chicony" on the forums shows that this is a common problem, without an obvious fix:

[http://ubuntuforums.org/showthread.php?t=2093384&highlight=Chicony](http://ubuntuforums.org/showthread.php?t=2093384&highlight=Chicony)

Are there any module (or kernel) switches for the uvc video driver?

Some helpful advice from this site:  

[http://www.ideasonboard.org/uvc/#footnote-3](http://www.ideasonboard.org/uvc/#footnote-3)

"Hold the computer upside down."

---

### Post by rooney09 on 2013-01-03
I wish my web camera driver works as cool as your humor does :)
Am I wrong or as I saw there is no chicony web cam driver release for 12.10?
I also checked out and tried all these links which you gave me but it seems that neither of them work :S

> Name: Chicony Electronics Co., Ltd 2.0M UVC Webcam / CNF7129

Ubuntu releases: 10.04 LTS

At least I got this:

```
Module                  Size  Used by
joydev                 17457  0 
snd_hda_codec_via      46599  1 
coretemp               13400  0 
rfcomm                 46619  0 
snd_hda_intel          33491  3 
snd_hda_codec         134212  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                96580  2 snd_hda_intel,snd_hda_codec
microcode              22803  0 
psmouse                95552  0 
bnep                   18140  2 
arc4                   12529  2 
parport_pc             32688  0 
serio_raw              13215  0 
bluetooth             209199  10 rfcomm,bnep
ppdev                  17073  0 
snd_seq_midi           13324  0 
snd_rawmidi            30512  1 snd_seq_midi
ath9k                 131316  0 
uvcvideo               76749  0 
videobuf2_core         32851  1 uvcvideo
videodev              120309  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12860  1 uvcvideo
binfmt_misc            17500  1 
videobuf2_memops       13368  1 videobuf2_vmalloc
mac80211              539908  1 ath9k
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29425  2 snd_pcm,snd_seq
ath9k_common           14055  1 ath9k
ath9k_hw              395218  2 ath9k,ath9k_common
ath                    23827  3 ath9k,ath9k_common,ath9k_hw
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              206566  3 ath9k,mac80211,ath
asus_laptop            24722  0 
sparse_keymap          13890  1 asus_laptop
i915                  520539  3 
snd                    78734  15 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
input_polldev          13896  1 asus_laptop
mac_hid                13205  0 
lpc_ich                17061  0 
drm_kms_helper         49112  1 i915
drm                   288670  4 i915,drm_kms_helper
i2c_algo_bit           13413  1 i915
soundcore              15047  1 snd
video                  19335  1 i915
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
lp                     17759  0 
parport                46345  3 parport_pc,ppdev,lp
hid_generic            12493  0 
usbhid                 46947  0 
hid                   100366  2 hid_generic,usbhid
atl1e                  33208  0 
```

---

### Post by tgalati4 on 2013-01-03
Several webcameras are stuffed into uvc--USB video camera driver.  This is a generic, catch-all driver that supports several webcams.  The link I posted shows the current status of that driver and does show upsidedown video for your camera.  It includes the helpful note about turning the camera upside down.

If you are handy, you can take your screen apart and physically turn the camera right side up.  The fact that you needed a special Windows driver hints that the camera was installed upside down.

The alternative is to flip the video in real time.  And I am thinking outloud here . . .

ffmpeg -i /dev/video0 -top 0 /dev/video1

Then select /dev/video1 for your application.

Or, try to get a hold of this guy (from a 2009 thread) and see if he can offer suggestions.

[https://lists.berlios.de/pipermail/linux-uvc-devel/2009-June/004886.html](https://lists.berlios.de/pipermail/linux-uvc-devel/2009-June/004886.html)

Get familiar with these tools:

qv4l2 - Graphical Qt v4l2 control panel
uvcdynctrl - Command line tool to control v4l2 devices
uvcdynctrl-data - Command line tool to control v4l2 devices - data files
uvcdynctrl-dbg - Debug Symbols for uvcdynctrl
v4l-conf - tool to configure video4linux drivers
v4l-utils - Collection of command line video4linux utilities
v4l2loopback-dkms - Source for the v4l2loopback driver (DKMS)
v4l2loopback-source - Source for the v4l2loopback driver
v4l2loopback-utils - Commandline utilities for the for the v4l2-loopback module
v4l2ucp - Video for Linux 2 Universal Control Panel

uvcdynctrl--this sounds like a tool to dynamically control uvc devices--something that you are trying to do.

```
sudo apt-get install uvcdynctrl
man uvcdynctrl
uvcdynctrl
```

---

### Post by rooney09 on 2013-01-03
When I type this:
> ffmpeg -i /dev/video0 -top 0 /dev/video1

Then select /dev/video1 for your application.

I get this:

```
ffmpeg version 0.8.4-6:0.8.4-0ubuntu0.12.10.1, Copyright (c) 2000-2012 the Libav developers
  built on Nov  6 2012 16:51:11 with gcc 4.7.2
[COLOR="DarkOrange"]*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.[/COLOR]
**[COLOR="Red"]/dev/video0: Operation not permitted[/COLOR]
```**
So, I guess this is not a viable way.

After installing the v4l2ucp package and getting in the control panel, I ticked the Vertical flip but sadly nothing has changed.
[Screen-shot](http://img833.imageshack.us/img833/7762/screenshotfrom201301040.png)

About the ```
uvcdynctrl
``` one, I am not quite sure how to modify and what to modify cause when I type ```
uvcdynctrl -c
``` I only see these options:

```
Listing available controls for device video0:
  Brightness
  Contrast
  Saturation
  Hue
  White Balance Temperature, Auto
  Gamma
  Gain
  Power Line Frequency
  White Balance Temperature
  Sharpness
  Backlight Compensation
```

and I guess there is no option to invert the camera.

P.S. About Hans, I will mail him if we don't make it.

---

### Post by coldcritter64 on 2013-01-03
OP I notice you tried the vertical flip, did you also try the horizontal flip ? (that is the one I would try in your situation). I would have thought upside down video as being horizontally flipped ;)

---

### Post by evilsoup on 2013-01-03
That looks like a permission problem; I guess you could try running ffmpeg as root (though you shouldn't need to). First try this command:

```

ffmpeg -f video4linux2 -i /dev/video0 -top 0 -f video4linux2 /dev/video1

```

If that spits up the same error, try running it with sudo

```

sudo ffmpeg -f video4linux2 -i /dev/video0 -top 0 -f video4linux2 /dev/video1

```

---

### Post by FakeOutdoorsman on 2013-01-03
Maybe the "v4l1compat.so" solution in this bug report will help.
[url=https://answers.launchpad.net/ubuntu/+source/skype/+question/195310]
Webcam is not working on skype with Ubuntu 12.04[/url]

---

### Post by rooney09 on 2013-01-03
> OP I notice you tried the vertical flip, did you also try the horizontal flip ? (that is the one I would try in your situation). I would have thought upside down video as being horizontally flipped 
Neither of them works.

> **evilsoup said:**
> That looks like a permission problem; I guess you could try running ffmpeg as root (though you shouldn't need to). First try this command:

```

ffmpeg -f video4linux2 -i /dev/video0 -top 0 -f video4linux2 /dev/video1

```

If that spits up the same error, try running it with sudo

```

sudo ffmpeg -f video4linux2 -i /dev/video0 -top 0 -f video4linux2 /dev/video1

```

Alright, here is what I have now:
```
ffmpeg version 0.8.4-6:0.8.4-0ubuntu0.12.10.1, Copyright (c) 2000-2012 the Libav developers
  built on Nov  6 2012 16:51:11 with gcc 4.7.2
[COLOR="DarkOrange"]*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
[video4linux2 @ 0x1847900] Estimating duration from bitrate, this may be inaccurate[/COLOR]
Input #0, video4linux2, from '/dev/video0':
  Duration: N/A, start: 5343.206661, bitrate: 147456 kb/s
    Stream #0.0: Video: rawvideo, yuyv422, 640x480, 147456 kb/s, 30 tbr, 1000k tbn, 30 tbc
Requested output format 'video4linux2' is not a suitable output format

```

I've just experimented while the camera was turned on and I received this as output x]

```
ffmpeg version 0.8.4-6:0.8.4-0ubuntu0.12.10.1, Copyright (c) 2000-2012 the Libav developers
  built on Nov  6 2012 16:51:11 with gcc 4.7.2
[COLOR="DarkOrange"]*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.[/COLOR]
[COLOR="Red"][B][video4linux2 @ 0x25c2900] Cannot find a proper format for codec_id 0, pix_fmt -1.
/dev/video0: Input/output error[/B][/COLOR]
```

---

### Post by rooney09 on 2013-01-03
> **FakeOutdoorsman said:**
> Maybe the "v4l1compat.so" solution in this bug report will help.
[url=https://answers.launchpad.net/ubuntu/+source/skype/+question/195310]
Webcam is not working on skype with Ubuntu 12.04[/url]

Okay I think this seems to work ..
When I typed:

```
sudo apt-get install libv4l-0
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype
```

The skype has opened and the camera inthere was fine (except this one in the options menu - it shows a black screen).
Let me give you a [Screen-shot](http://img571.imageshack.us/img571/7762/screenshotfrom201301040.png) to see what I am talking about.

But when I close it and restart it (this time by the shortcut left on my desktop) I am again with the upside down.

EDIT: Finally! 

I found ```
Exec=skype
``` and replaced it with ```
Exec=bash -c 'LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype'
```

Now it works with one word - brilliantly :)
Many thanks for the help guys and I am sorry if I disturbed you too much.

---

### Post by evilsoup on 2013-01-03
That's alright, this stuff is the whole point of the forum.

Please mark the thread as 'solved' using the thread tools at the top of the page.

---

