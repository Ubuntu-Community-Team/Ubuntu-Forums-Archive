---
title: "Convertin any video format to 3gp format"
date: 2011-07-21
forum: Multimedia Software
---

### Post by subchief on 2011-07-21
Guys i need help converting videos to 3gp format.

i have installed transmaggedon software but it fails to convert because quicktime muxer plugin is not installed.

This plugin is not available in the repositories.

How can i get this video converter to work or what else can i do to be able to convert videos to 3gp format?

Thank u!!!

---

### Post by andrew.46 on 2011-07-22
The 3gp container can hold a quite limited range of codecs, [see here]("http://en.wikipedia.org/wiki/3GP_and_3G2#Technical_details") for some details. The most compatible pair of codecs would be h263 for the video and amr for the sound, although quality for both of these is never great. A sample commandline for this combination, using FFmpeg, is as follows:

```

ffmpeg -i <input_file> \
       -s qcif -vcodec h263 \
       -acodec libopencore_amrnb -ac 1 -ar 8000 -r 25 -ab 12200 \
       <output_file>

```

This will be ok on an older mobile phone for example but newer devices will support aac sound which will make a huge improvement to playback. Lots of room for experimentation there with the device you wish to use for playback and the codecs available to you :).

---

### Post by sectshun8 on 2011-07-22
Can't you convert it in OpenShot?  Import the file, add it to the timeline, then export it as .3gp and the correct audio codec in the Advanced tab.

---

