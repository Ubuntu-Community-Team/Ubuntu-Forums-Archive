---
title: "Four v4l2 and ffmpeg (streamcopy) video manipulation scripts"
date: 2018-02-27
forum: Multimedia Software
---

### Post by xinuzi on 2018-02-27
[SIZE=4]**1. Requirements**[/SIZE]

- v4l-utils (v4l2-ctl)
- FFmpeg

[SIZE=4]**2. Scripts**[/SIZE]

Save the scripts seperately with the .sh extension and make them Owner & Group executable.

[SIZE=3]**2.1 Set Video4Linux input device (e.g. Easycap videostick) image quality for recording/capturing**[/SIZE]

The quality of an input device video isn't always what it could be.
Manipulating it with v4l2 can be delicate.

Check the default settings of the input device first with: v4l2-ctl -d /dev/video1 -l .
Most often only the brightness and the saturation need to be set.

Example of possible settings of input device:

User Controls

brightness (int): min=0 max=1023 step=1 default=448 value=448 flags=slider
contrast (int): min=0 max=1023 step=1 default=464 value=464 flags=slider
saturation (int): min=0 max=1023 step=1 default=512 value=512 flags=slider
hue (int): min=-3583 max=3583 step=1 default=0 value=0 flags=slider
sharpness (int): min=0 max=255 step=1 default=96 value=96 flags=slider

And the script that manipulates these settings just slightly with a much better video image as a result:

```
#!/bin/bash

# Set correct input device (video0, video1)...
# Easycap Default settings: brightness=448,contrast=464,saturation=512,hue=0,sharpness=96

v4l2-ctl -d /dev/video1 -c brightness=449,contrast=464,saturation=506,hue=0,sharpness=96

exit

```

Use the settings that work best for your input device an place the script on e.g. your desktop.
If you want to record with e.g. VLC or OBS, open one of those programs and click your script to see the 
result.
In VLC you click 'Play' after clicking the script. This will give you the requested video image quality to record (Convert/Save)
to e.g. mkv, 1800 kbps, fps as is, mpeg4, 640x360 or 1280x720, mpeg2audio or default audio of video (mp3 and aac don't always record well in VLC). 
Converting just the audio with e.g. Avidemux afterwards doesn't take too much time. In the VLC extended settings you can 
set the same v4l2-ctl things like this {brightness=449,saturation=506} (input/codecs, accessmodules, V4L, v4l driver manipulation-sth at the right side bottom) but they don't always immediately work. Therefore: the script.

[SIZE=3]**2.2 Merge**[/SIZE]

Join movies of same video and audio format, bitrate and speed to 1 movie.
Requires specific dir (where you place the to be joined files) and absolute dir path.

```
#!/bin/bash

ffmpeg -f concat -safe 0 -i <(printf "file '%s'\n" /home/User/Videos/FFmpeg_Merge/*.mkv) -c copy merged.mkv

exit

```

[SIZE=3]**2.3 Synchronize video and audio and set dar (Display Aspect Ratio) simultaneously**[/SIZE]

Many struggle with desynchronized lip movements in their videos. Setting another fps (frames per second) than 
that of the input is most often the cause.
This script works very well in as good as all cases.
The dar setting can be useful for those recording PAL or SECAM. It gives a more modern HD-look to videos.

```
#!/bin/bash

for i in *.mkv; do ffmpeg -i "$i" -itsoffset 0.2 -i "$i" -map 0:0 -map 1:1 -aspect 16:9 -c copy "${i%.*}_synced_darred.mkv"; done

exit

```

Place in any dir together with the to be synced + darred videos.

[SIZE=3]**2.4 Change video container and dar simultaneously**[/SIZE]

```
#!/bin/bash

# Attention, this doesn't always work with conversion to mkv

for i in *.avi; do ffmpeg -i "$i" -aspect 16:9 -c copy "${i%.*}_converted.mp4"; done

exit

```

Place in any dir where you want to change the container of the avi-files.

I prefer the flexible, open mkv-container, but I've noticed that it didn't work so well with this avi-to-other-script.
Solution: change avi-container to mp4 first and afterwards possibly mp4 to mkv with two script files.

Input codec mpeg4 combined with mp3 or x264 combined with aac are good choices for mkv.
Mpeg4 has the advantage of making aftercutting (on keyframes! in Avidemux e.g.) easier.

There you are.
Hope this helps you video-fiddlers as much as myself.

---

