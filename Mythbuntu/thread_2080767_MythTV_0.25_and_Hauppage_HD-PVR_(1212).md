---
title: "MythTV 0.25 and Hauppage HD-PVR (1212)"
date: 2012-11-04
forum: Mythbuntu
---

### Post by two4two on 2012-11-04
OK, probably this has been dealt with already, but looking thru the first several pages of threads doesn't give me an answer.  I look in the Wiki, and the MythTV manual, and it doesn't explain how to get it working if ALL I want to do is record my VHS tapes into my computer using the HD-PVR as my capture device.  It always wants me to define video source, like I'm subscribing to some service such as Comcast, or Dish network.  But I'm not.  I'm simply recording from my video tapes.  I get the error that it can't connect to the master backend server, but that won't start because it has no video source defined.  Anyway, does anyone know how to set this up so I can record from my video tapes?  Thanks.

---

### Post by nickrout on 2012-11-05
> **two4two said:**
> OK, probably this has been dealt with already, but looking thru the first several pages of threads doesn't give me an answer.  I look in the Wiki, and the MythTV manual, and it doesn't explain how to get it working if ALL I want to do is record my VHS tapes into my computer using the HD-PVR as my capture device.  It always wants me to define video source, like I'm subscribing to some service such as Comcast, or Dish network.  But I'm not.  I'm simply recording from my video tapes.  I get the error that it can't connect to the master backend server, but that won't start because it has no video source defined.  Anyway, does anyone know how to set this up so I can record from my video tapes?  Thanks.This has nothing to do with mythtv if all you want to do is record from an external source like a VCR. 

However it can be done, you need to create a dummy video source and pair it to the HDPVR. Then create a manual recording for the expected time of the VCR you want to transcribe.

---

### Post by two4two on 2012-11-05
The reason I am using MythTV is because they said it is the way Linux supports the device.  They said without it there would be no driver or firmware available.  That being said, eventually I will have a DVB source and then use satellite as another input, but I still can't see why MythTV desperately needs me to define an input source.  Even with the satellite input, here in the good old US of A, unless I sign up for DirectTV or Dish, there is no "provider" to speak of.  It is the FTA end of it I'll be interested in, and so in that case it'll be the same situation as I have now.  I simply don't have a "provider".

Now, "set up a dummy source"?  How to do that?  MythTV will try to go to the web site of my "provider" and download the guide.  

There is the thing they call "XMLTV".  But in the backend setup there is no way to specify it.  My choices are "no grabber", "SchedulesDirect" or "transmitted guide".  None of those seem appropriate.  Without a grabber I get the error that says I haven't specified a source.  I don't have a Schedules Direct account and won't get one.  "Transmitted guide"?  I don't have a tuner.  So that leaves me to fake a source -- which is what you've alluded to.  Any way to do that?

Thank you for your help.

---

### Post by klc5555 on 2012-11-05
nickrout was right from the get-go, because setting up all of mythtv _just_ for this sort of VCR capture has got to be a waste of time and resources.

The drivers for this device have been includes in the linux kernel since about 2.6.30. No need any longer to compile anything.

The basic procedure for your VCR capture would consist of attaching a set of composite or component cables from the output of your VCR to the corresponding input of the PVR 1212. Then, use the procedure normally used for "testing" the 1212 to instead capture a recording playing from your VCR. That is ( [http://www.mythtv.org/wiki/Hauppauge_HD-PVR_1212](http://www.mythtv.org/wiki/Hauppauge_HD-PVR_1212) ):

> Testing the Driver

Even if you didn't compile your own kernel module, you should always test your box outside of MythTV before trying inside of MythTV. Once the module has loaded successfully, you can check dmesg for output and to determine which /dev/video node it has created. You can then test the device as with any hardware encoder:

cat /dev/video1 > test.ts

Press your interrupt character (usually ctrl-C) to stop the capture, and play it back with any compatible media player (i.e., mplayer, xine, mythfrontend).

For you, "test.ts" will end up being your recorded video. You can watch it while the capture is in process (in case tape problems crop up) with xine or mplayer, and you can trim off the usual extra junk that is likely to be at the start or end of a VCR video by using a simple video editing program like avidemux.

If the 1212 does not recognize which input is being used, it is supposed to be compatible with the old command-line ivtv-utils, which would imply that you could specify this by using the v4l2-ctl utility in the ivtv-utils.

---

### Post by nickrout on 2012-11-05
> **two4two said:**
> The reason I am using MythTV is because they said it is the way Linux supports the device.  They said without it there would be no driver or firmware available.  That being said, eventually I will have a DVB source and then use satellite as another input, but I still can't see why MythTV desperately needs me to define an input source.  Even with the satellite input, here in the good old US of A, unless I sign up for DirectTV or Dish, there is no "provider" to speak of.  It is the FTA end of it I'll be interested in, and so in that case it'll be the same situation as I have now.  I simply don't have a "provider".

Now, "set up a dummy source"?  How to do that?  MythTV will try to go to the web site of my "provider" and download the guide.  

There is the thing they call "XMLTV".  But in the backend setup there is no way to specify it.  My choices are "no grabber", "SchedulesDirect" or "transmitted guide".  None of those seem appropriate.  Without a grabber I get the error that says I haven't specified a source.  I don't have a Schedules Direct account and won't get one.  "Transmitted guide"?  I don't have a tuner.  So that leaves me to fake a source -- which is what you've alluded to.  Any way to do that?

Thank you for your help.You need to set up a source becuase mythtv is designed to record TV and to do so needs a listing (obviously). 

"No grabber" is the correct one for your usage.

When you get satellite you will obviously need a listings garbber, you will need a schedules direct account if you are in the US. myth changes the channel on your stb in that setup.

But doesn't ```
cat /dev/video0 > videofile.mpg
``` just work?

---

### Post by two4two on 2012-11-05
Thanks everyone for helping.  the cat command doesn't exactly work.  It certainly produces a file, but the file has no properties video properties.  It's a nice-sized file when I try it for a minute or so, it just has no video properties and so mplayer can't play it.  Also, it has no audio.  I'm thinking the default is to use the component inputs and the audio inputs on the back of the unit (or maybe the SPDIF?), but my VCR is connected to the S-Video input and the PCM audio on the front of the box.  If I knew how to specify to use these maybe the capture would actually get some input.  Anyone know where to learn how to do this?

Also, MythTV docs for the HD-PVR say to don't use an external software because it'll make the driver unstable.  So now that I tried the cat command the backend setup can't probe the device.  So I think I need to power it off and maybe re-boot?

---

### Post by nickrout on 2012-11-05
> **two4two said:**
> Thanks everyone for helping.  the cat command doesn't exactly work.  It certainly produces a file, but the file has no properties video properties.  It's a nice-sized file when I try it for a minute or so, it just has no video properties and so mplayer can't play it.  Also, it has no audio.  I'm thinking the default is to use the component inputs and the audio inputs on the back of the unit (or maybe the SPDIF?), but my VCR is connected to the S-Video input and the PCM audio on the front of the box.  If I knew how to specify to use these maybe the capture would actually get some input.  Anyone know where to learn how to do this?I believe you need to use v4l2-ctl. Start with ```
v4l2-ctl --all
```You will need to set the appropriate inputs> 

Also, MythTV docs for the HD-PVR say to don't use an external software because it'll make the driver unstable.  So now that I tried the cat command the backend setup can't probe the device.  So I think I need to power it off and maybe re-boot?

---

### Post by two4two on 2012-11-07
Thanks everyone.  I've been playing with v4l2-ctl and sometimes it tells me the control is invalid.  But I'm researching and hopefully will understand it soon.  I'm playing with ffmpeg to do the capture.  I found a script on Phyrne's Blog.  Not sure if it's appropriate for Ubuntu but I'm going to try it.  I'd still like to preview while it's capturing.  After I get capture to work I'll post what I did and ask how to do the preview.

---

### Post by nickrout on 2012-11-07
> **two4two said:**
> Thanks everyone.  I've been playing with v4l2-ctl and sometimes it tells me the control is invalid.  But I'm researching and hopefully will understand it soon.  I'm playing with ffmpeg to do the capture.  I found a script on Phyrne's Blog.  Not sure if it's appropriate for Ubuntu but I'm going to try it.  I'd still like to preview while it's capturing.  After I get capture to work I'll post what I did and ask how to do the preview.```
cat /dev/video0 |tee file.mpg|mplayer -
```

tee writes the stream to a file and to STDOUT. mplayer - plays STDIN. So you get the stream playing in mplayer and saved to file.mpg.

---

### Post by two4two on 2012-11-11
OK, I'm going to close this thread as resolved.  And I'd ask the moderator to either move it to the correct forum or to delete it if there is no such forum or he (or she) doesn't have the authority or the time or the interest.  I think it'd be a valuable thread in the correct forum.

Here's my resolution:  I am not using MythTV for this purpose (per several replies here.)  However I WILL use MythTV once I get my satellite FTA DVB-S2 system.  I have taken the advice of replies here and am using ffmpeg command line to record.  It works great and the HD-PVR works great too!  mplayer has the capability to do it, and supposedly so does MLT (but I haven't verified it).

Thanks all and I do hope the moderator finds a good home for this thread.

My commands:
# Audio IN 0=RCABack 1=RCAFront 2=SPDIF

# Video Input IN 0=component, 1=s-vid1(front) 2=composite1(front) 

# video bitrate mode 0=VBR, 1-CBR

# audio_encoding [3=AAC - 4=AC3]
v4l2-ctl --verbose -d /dev/video1 -c audio_encoding=4 

v4l2-ctl --verbose -d /dev/video1 --set-audio-input=1

v4l2-ctl --verbose -d /dev/video1 --set-input=1

v4l2-ctl --verbose -d /dev/video1 -c video_bitrate_mode=1

v4l2-ctl --verbose -d /dev/video1 -c video_bitrate=13500000

v4l2-ctl --verbose -d /dev/video1 -c video_peak_bitrate=20200000

v4l2-ctl --verbose -d /dev/video1 --set-ctrl brightness=125 --set-ctrl contrast=60 --set-ctrl hue=15 --set-ctrl saturation=85 --set-ctrl sharpness=130





# to capture:
ffmpeg -i /dev/video1 -vcodec copy -acodec ac3 -ab 448k ~/capture.mp4

---

### Post by nickrout on 2012-11-11
> **two4two said:**
> OK, I'm going to close this thread as resolved.  And I'd ask the moderator to either move it to the correct forum or to delete it if there is no such forum or he (or she) doesn't have the authority or the time or the interest.  I think it'd be a valuable thread in the correct forum.

Here's my resolution:  I am not using MythTV for this purpose (per several replies here.)  However I WILL use MythTV once I get my satellite FTA DVB-S2 system.  I have taken the advice of replies here and am using ffmpeg command line to record.  It works great and the HD-PVR works great too!  mplayer has the capability to do it, and supposedly so does MLT (but I haven't verified it).

Thanks all and I do hope the moderator finds a good home for this thread.

My commands:
# Audio IN 0=RCABack 1=RCAFront 2=SPDIF

# Video Input IN 0=component, 1=s-vid1(front) 2=composite1(front) 

# video bitrate mode 0=VBR, 1-CBR

# audio_encoding [3=AAC - 4=AC3]
v4l2-ctl --verbose -d /dev/video1 -c audio_encoding=4 

v4l2-ctl --verbose -d /dev/video1 --set-audio-input=1

v4l2-ctl --verbose -d /dev/video1 --set-input=1

v4l2-ctl --verbose -d /dev/video1 -c video_bitrate_mode=1

v4l2-ctl --verbose -d /dev/video1 -c video_bitrate=13500000

v4l2-ctl --verbose -d /dev/video1 -c video_peak_bitrate=20200000

v4l2-ctl --verbose -d /dev/video1 --set-ctrl brightness=125 --set-ctrl contrast=60 --set-ctrl hue=15 --set-ctrl saturation=85 --set-ctrl sharpness=130





# to capture:
ffmpeg -i /dev/video1 -vcodec copy -acodec ac3 -ab 448k ~/capture.mp4Out of curiosity did the previously documented method ```
cat /dev/video1 >file.mpg
```ever work?

By the way the thread can probably stay here - google will find it for people having the same question :)

---

### Post by two4two on 2012-11-13
Yes, both of these work:

cat /dev/video? >file.mpg
cat /dev/video? |tee file.mpg|mplayer -

"tee" gives preview, but it is jumpy even though I have a current technology mobo with 6-core 3.3g AMD 11T processor and 12g ram.

After I learned to use v4l2-ctl to set the correct inputs everything fell into place.  I have an internal capture card so sometimes I get a different number for /dev/video?.  But it does capture component video very well.

Thank you all for your help.  After I get my DVB-S2 receiver card I'm sure I'll be back asking for MythTV help, unless I just do it all with Mplayer or VLC or something like that, but I'd like to be able to set timers, etc.

---

