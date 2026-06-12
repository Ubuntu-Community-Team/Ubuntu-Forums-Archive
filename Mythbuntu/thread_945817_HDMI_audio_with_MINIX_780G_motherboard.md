---
title: "HDMI audio with MINIX 780G motherboard"
date: 2008-10-12
forum: Mythbuntu
---

### Post by jape42 on 2008-10-12
Hi Folks,

I'm trying to get HDMI audio working with this MB:
[http://www.jwele.com/motherboard_detail.php?419](http://www.jwele.com/motherboard_detail.php?419)

After much playing around :

jape@vcr3:/dev$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


I figured out that the correct setting in mythtv is:

ALSA:hw:1,3

For the playback device.

The problem is that this will only work if I manually mute and then unmute the IEC958 device from the command line:

amixer -c 1 sset 'IEC958' mute
amixer -c 1 sset 'IEC958' unmute

Is there anyway I can get mythtv to do this for me when I start playback?

Any thoughts or other pointers appreciated.

jp

---

### Post by JugeHuge on 2008-10-13
Here is solution that solved all my HDMI audio problems:[No sound over HDMI with ga-ma78gm-s2h AMD 780G motherboard]("http://www.gossamer-threads.com/lists/mythtv/users/333112#333112")

---

### Post by jape42 on 2008-10-13
> **JugeHuge said:**
> Here is solution that solved all my HDMI audio problems:[No sound over HDMI with ga-ma78gm-s2h AMD 780G motherboard]("http://www.gossamer-threads.com/lists/mythtv/users/333112#333112")

Thanks for the tip. With the new .asoundrc file, I can now use the ALSA:default output device in myth (instead of hw:1,3) but I still have the muting problem.  

Interstingly, mplayer has no muting problem.  For example this works fine  repeatedly:

 mplayer -ao alsa 1064_20080701133000.mpg 

This is a real head scratcher, unless there is a bug or something missing in mythtv?  Perhaps myth fails to do the muting/unmuting if it can't find the mixer device?:

2008-10-13 08:34:54.737 Opening audio device 'default'. ch 2(2) sr 48000
2008-10-13 08:34:54.737 Opening ALSA audio device 'default'.
2008-10-13 08:34:54.762 Mixer unable to find control Master
2008-10-13 08:34:54.762 Mixer unable to find control Master
2008-10-13 08:34:54.762 Mixer unable to find control PCM
2008-10-13 08:34:54.762 Mixer unable to find control PCM
2008-10-13 08:34:54.762 Mixer unable to find control PCM

---

### Post by JugeHuge on 2008-10-13
try unmuting IEC958 with alsamixer and then try 'alsactl store' command.

---

### Post by jape42 on 2008-10-13
> **JugeHuge said:**
> try unmuting IEC958 with alsamixer and then try 'alsactl store' command.


No luck unfortunately with the above.  The device is always unmuted as far as alsamixer can tell, but for some reason I get no audio unless I mute/unmute it.

Found another thread on this, but no solution:

[http://www.mediaboxblog.co.uk/blog1.php/2008/08/15/howto-audio-over-hdmi-with-the-hd3200-rs](http://www.mediaboxblog.co.uk/blog1.php/2008/08/15/howto-audio-over-hdmi-with-the-hd3200-rs)

---

### Post by nwpowell on 2008-10-13
> **jape42 said:**
> No luck unfortunately with the above.  The device is always unmuted as far as alsamixer can tell, but for some reason I get no audio unless I mute/unmute it.

Found another thread on this, but no solution:

[http://www.mediaboxblog.co.uk/blog1.php/2008/08/15/howto-audio-over-hdmi-with-the-hd3200-rs](http://www.mediaboxblog.co.uk/blog1.php/2008/08/15/howto-audio-over-hdmi-with-the-hd3200-rs)

I was able to fix this problem on my Myth box by switching to the radeonhd driver per the instructions in the link you referenced above.  I haven't been able to get the video to run as smoothly as with the catalyst drivers but I haven't had time to mess with it either.

---

### Post by JugeHuge on 2008-10-14
Strange indeed.. funny that mplayer doesn't have muting problem and mythtv does.. :(

---

### Post by jape42 on 2008-10-17
> **nwpowell said:**
> I was able to fix this problem on my Myth box by switching to the radeonhd driver per the instructions in the link you referenced above.  I haven't been able to get the video to run as smoothly as with the catalyst drivers but I haven't had time to mess with it either.

I tried the radeonhd driver + patch to enable HDMI audio and it doesn't have the mute/unmute problem, but since Xvideo is not supported for my HD3200 onboard chipset, this results is choppy video playback. 

To be honest though, I like the radeonHD driver better than the catalyst.  No fighting, corrupted video, blank screens that I was seeing with the catalyst drivers.  Getting a 1:1 pixel mapping on my 1080p60 TV was trivial with radeonHD and never accomplished with catalyst.


regards

jp

---

