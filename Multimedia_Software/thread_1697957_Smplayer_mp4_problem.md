---
title: "Smplayer mp4 problem"
date: 2011-03-01
forum: Multimedia Software
---

### Post by hnasiet on 2011-03-01
I started using smplayer but there was a problem, youtube mp4 downloaded videos have no video playback, only sound, however other mp4 files play correctly. But when I use mplayer it plays correctly with video and audio.

---

### Post by tommcd on 2011-03-01
If it works with MPlayer, then it should be able to make it work with Smplayer. Here is a suggestion:
Try playing the problematic video file(s) from the terminal using mplayer like this:
```
mplayer video_name
```
Somewhere in the terminal output of MPlayer there will be the audio and video output drivers that are being used. For example, if I play a divx (.avi) file, here is what I get toward the end of the mplayer terminal output:
```

==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 48000 Hz, 2 ch, s16le, 112.0 kbit/7.29% (ratio: 14000->192000)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
Movie-Aspect is 1.77:1 - prescaling to correct movie aspect.
**VO: [xv] 624x352 => 624x352 Planar YV12** 

``` 
I have highlighted in **bold** the relevant info.
Then open up Smplayer and go to: preferences > video tab. For the output driver, try switching the output driver to what is listed in the terminal output for MPlayer. In my example above it would be **[xv]**. Click "apply", after making the selection, then see if your video will play.
Hope this helps.
Do other videos play properly in Smplayer?

---

### Post by hnasiet on 2011-03-02
```
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
AUDIO: 44100 Hz, 2 ch, s16le, 125.6 kbit/8.90% (ratio: 15694->176400)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Starting playback...
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [vdpau] 480x360 => 480x360 Planar YV12
```

I changed to vdpau but the problem remains, other videos like avi work, but what's strange is that one video (mp4) that was not downloaded from YT has the same video codec as the videos that give me the problem but it plays correctly.


```
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
AUDIO: 48000 Hz, 2 ch, s16le, 253.4 kbit/16.50% (ratio: 31671->192000)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [vdpau] 854x480 => 854x480 Planar YV12 
```
Edit:
I just downloaded a 1080p  mp4 video from youtube and it played properly. Is it some problem related to the resolution?

---

### Post by tommcd on 2011-03-03
> **hnasiet said:**
> 

VO: [vdpau] 854x480 => 854x480 Planar YV12 

I just downloaded a 1080p  mp4 video from youtube and it played properly. Is it some problem related to the resolution?
Well, I suppose it could be. I guess you would have to try a number of videos with different resolutions to rule this out.
I don't have any other ideas to try here. If I find something I will post back.

---

### Post by hnasiet on 2011-03-03
I can also play mp4 files with a lower resolution. If this helps this is how it looks like, it just doesn't play the video:
[IMG]http://img22.mediafire.com/5508095afdc481101c746ae9e87db54c2f4da7c407e7c5f7cb61a49acc8e82114g.jpg[/IMG]

Edit: Solved, deleted the ini file opened a random video and when the window that asks for mplayer version appears I chose version 1.0 rc3 or more recent I had put version 1.0 rc1 or more recent, don't know how the hell this solved the problem, but it's solved. XD

---

### Post by hnasiet on 2011-03-12
something strange happened. The problem returned after playing some files. then I deleted smplayer.ini again, nothing happened. But when I deleted file_settings it was fixed (that I also have deleted the first time but didn't associate with the fix). Gotta try to recreate the problem to fix it permanently.
Also, my Mplayer version is 2:1.0~rc4~try1.dsfg1-1ubuntu1+medibuntu1 which isn't recognized by mplayer, that's why that window appears.

Edit: just recreated the problem, it happens when I play a video with that resolution and format for the second time. If I turn off the option to save definition for each file it doesn't happen, but I love that feature so I would like a permanent fix.

---

### Post by stanoc on 2011-04-10
I had the same problem with a video from youtube and I found out a workaround. It seems that the video track number is not properly specified in the video file (probably uses number 1 instead of 0 regardless that no track number 0 exists). Smplayer then saves the settings for file as having only one track, thus number 0 is used. When trying to play the file once again, smplayer chooses the non-existing track number 0 and plays no video. 

If you change the line in
$HOME/.config/smplayer/file_settings/[path_to_ini_settings_file_of_the_problematic_video]

from
```
current_video_id=0
```

to
```
current_video_id=1
```

it should solve the problem for this specific video (no need to turn off the feature).

---

### Post by hnasiet on 2011-04-27
thanks, it fixes the problem, however I download videos regularly (I noticed I get the same problem with mkv videos) so changing it in every video that I download is just wasting time. I don't always need this feature so when I need it I turn it on when I don't turn it off. I will just wait for the next release to get this fixed.

---

### Post by tommcd on 2011-04-28
In the smplayer playlist configuration, try unchecking "*save copy of playlist on exit*".
I don't know if this will fix it; but it can't hurt anything.

---

### Post by dsmo223 on 2011-07-13
> **stanoc said:**
> 
If you change the line in
$HOME/.config/smplayer/file_settings/[path_to_ini_settings_file_of_the_problematic_video]

from
```
current_video_id=0
```to
```
current_video_id=1
```it should solve the problem for this specific video (no need to turn off the feature).

I was having the same trouble, and this worked for me. I am new to linux, can you tell me if there is a way to write a script that would do this in ubuntu if I just run the script?

Thank you

---

### Post by JohnnyXedos on 2012-03-04
Hello, 

I tried this:

place the 

current_video_id=1 

intu the smplayer.ini file under the [%General] subsection.

it works so far.... 
I hope it stays that way.

---

