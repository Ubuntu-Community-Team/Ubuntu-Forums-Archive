---
title: "How to select correct stream in asf files ??"
date: 2006-11-22
forum: Multimedia &amp; Video
---

### Post by mat_london on 2006-11-22
Hi All,

I've been trying this for a few days now and think I know what the problem is, but not the answer.
I've got a Jumptv subscription and none of the Ubuntu moz plugins work embedded in the browser i.e. VLC, Mplayer or Totem.
However while the mplayer plugin is attempting to work it shows the url of the stream it is trying to access.
I've taken a screenshot while its doing this and copied the url into VLC, Mplayer & Totem and get streaming video from all of them.
JumpTV appears to be multi-stream mms-over-http which offers several possible streams according to bandwidth.
Mplayer & Totem automatically select the tiny low bandwidth version which is about an inch square and VLC selects the very high bandwidth stream which is probably too high bandwidth for my connection as after about 20 seconds I get 

[00000369] ffmpeg decoder error: more than 5 seconds of late video -> dropping frame (computer too slow ?)

With VLC you can see it choosing the highest possible stream for both audio and video like this:

[00000332] access_mms access: selecting stream[0x1] audio (69 kb/s)
[00000332] access_mms access: ignoring stream[0x2] audio (53 kb/s)
[00000332] access_mms access: ignoring stream[0x3] audio (26 kb/s)
[00000332] access_mms access: ignoring stream[0x4] audio (14 kb/s)
[00000332] access_mms access: selecting stream[0x5] video (940 kb/s)
[00000332] access_mms access: ignoring stream[0x6] video (321 kb/s)
[00000332] access_mms access: ignoring stream[0x7] video (102 kb/s)
[00000332] access_mms access: ignoring stream[0x8] video (52 kb/s)
[00000332] access_mms access: connection successful

My question is does anyone out there know how to either force VLC to select a slightly lower bandwidth - the one I want is the 321 kb/s video stream - or alternatively does anyone know how to force Mplayer or Totem to use a higher bandwidth stream. The -bandwidth option isn't working on Mplayer as it is used to restrict bandwidth not boost it.

Any thoughts or experience greatly appreciated.

Mat

---

### Post by TuxCrafter on 2006-12-23
I used this script on dapper but on edgy it doesn't work anymore maybe you can get it working can you pm me if you get it working?

```

#Name:		Play 3FM Radio
#Comment:	Script to get a media stream and play it
#Command:	xterm -e /mnt/hda3/muziek/3fm.sh

# This software is free software; you can redistribute it and/or modify it
# under the terms of the GNU General Public License as published by the
# Free Software Foundation; either version 2, or (at your option) any
# later version.
#
# This software is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.

#!/bin/sh

#sudo apt-get install mpg123
#sudo apt-get install mimms
#sudo apt-get install ffmpeg

#mimms mms://wm2.xs4all.nl/streamgate46 --output=3fm.asf
#ffmpeg -i ~/3fm.asf ~/3fm.mp3
#mpg123 -C -v ~/3fm.mp3

#mimms mms://wm2.xs4all.nl/streamgate46
#mimms mms://wm2.xs4all.nl/streamgate46 --output=3fm.asf | ffmpeg -i 3fm.asf ~/3fm.mp3 | mpg123 -C -v ~/3fm.mp3

cd ~/
rm ~/3fm.asf
#xterm -e "mimms mms://wm2.xs4all.nl/streamgate46 --output=3fm.asf" &
mimms -c -t 1440 mms://wm2.xs4all.nl/streamgate46 3fm.asf
sleep 10
ffplay -nodisp ~/3fm.asf
#xterm -e "ffplay -nodisp ~/3fm.asf" &

#exit

#mimms mms://wm2.xs4all.nl/streamgate46 --output=3fm.asf
#ffplay -nodisp ~/3fm.asf
```

---

### Post by richrosa on 2007-10-22
Did you ever find a solution to this?

---

### Post by TuxCrafter on 2007-10-22
Nope, to bad, I did not find if a solution for asf file. However i found a mpg stream of the radio station I wanted: [http://shoutcast2.omroep.nl:8104/](http://shoutcast2.omroep.nl:8104/)

---

