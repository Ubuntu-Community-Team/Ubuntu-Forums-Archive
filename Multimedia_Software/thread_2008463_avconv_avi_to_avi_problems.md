---
title: "avconv avi to avi problems"
date: 2012-06-22
forum: Multimedia Software
---

### Post by syerges on 2012-06-22
I'm trying to convert my movie files to .avi files that are compatible with both xbox and ps3. I don't understand why it's not working and I've tried everything. I have figured out that I have to use avconv to get decent quality but I'm going nuts.... here's the requirements:
File Extensions: .avi, .divx
Containers: AVI
Video Profiles: MPEG-4 Part 2, Simple & Advanced Simple Profile
Video Bitrate: 5 Mbps with resolutions of 1280 x 720 at 30fps.
Audio Profiles: Dolby® Digital 2 channel and 5.1 channel, MP3
Audio Max Bitrate: No restrictions.
I have a ton of codes that work for some video's and nothing works for others. The biggest thing is getting it to force to 30fps...HELP!

---

### Post by syerges on 2012-11-26
-f dvd -target ntsc-dvd -b 5000k -r 29.97 -vf scale=720:480 -acodec mp2 -ac 2 -ar 48000 -ab 192k

for ffmpeg not avconv and this doesn't include the input file or output file... but if anyone is looking for what I was, here it is! also works on directv:popcorn:

---

