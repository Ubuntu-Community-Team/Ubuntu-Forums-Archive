---
title: "[SOLVED] Video Encoder for Sony Walkman (NWZ-A728)"
date: 2008-11-16
forum: Multimedia Software
---

### Post by djbushido on 2008-11-16
Didn't know if there was anyone who could help me with video encoding for the Sony walkman on Linux. On windows, i used any video converter, which is mencoder, but couldn't get it running with wine. I then recompiled ffmpeg to support aac and x264, but that didn't work. If anybody has any idea on how to get video converting running, i would appreciate it, because printing and this are my last ties to windows.
Thank you for your help in advance!
By the way, all i know is that it needs x264 video and aac audio

---

### Post by FakeOutdoorsman on 2008-11-16
> **djbushido said:**
> Didn't know if there was anyone who could help me with video encoding for the Sony walkman on Linux. On windows, i used any video converter, which is mencoder, but couldn't get it running with wine.
Are you saying that you tried to get mencoder to run under Wine?  Why not just install mencoder from the repository?  If you like using a terminal:
```
sudo apt-get install mencoder
```
> I then recompiled ffmpeg to support aac and x264, but that didn't work.
Did ffmpeg fail to encode, or did the player not work with the video ffmpeg made?  Also include your ffmpeg command and the full ffmpeg response.
> If anybody has any idea on how to get video converting running, i would appreciate it, because printing and this are my last ties to windows.
Thank you for your help in advance!
By the way, all i know is that it needs x264 video and aac audio
You can take a video that already works in the player and find out what it's settings are:
```
ffmpeg -i videothatworks.mp4
```
You can use the specs that ffmpeg shows to help make a working video.

---

### Post by Keyper7 on 2008-11-16
I have absolutely no idea if it will work, but here is the mencoder line I use to convert a video for my Sony Ericsson k550i phone:

mencoder <input> -o <output> -of lavf -lavfopts format=mp4 -oac lavc -ovc lavc -lavcopts aglobal=1:vglobal=1:acodec=libfaac:abitrate=<audiobitrate>:vbitrate=<videobitrate>

Just replace <input>, <output>, <audiobitrate> and <videobitrate> with whatever you want.

PS: It might take an entire day to check your reply to this, but I will.

---

### Post by djbushido on 2008-11-16
Thank you for responding!
Anyway, I will try the ffmpeg -i thing.
To let you know, i did install mencoder via synaptic, i had tried to get any video converter running with wine, but that failed. Horribly.
Anyway, the mencoder line looks good, but i need to use x264, so i just need to replace libavc or whatever with libx264. I will try that, so thank you!

---

### Post by FakeOutdoorsman on 2008-11-16
Your player can handle 320x240 768k bitrate h264 videos.  You can try this setting for iPod, which has similar particularities.  First you will need to use a version of ffmpeg that can encode with libx264 and libfaac.  Either see [HOWTO: Compile the latest ffmpeg and x264 from source]("http://ubuntuforums.org/showthread.php?t=786095") or try (for Ibex only):
```
sudo apt-get update
sudo apt-get purge ffmpeg
sudo apt-get install libavcodec-unstripped-51 libavdevice-unstripped-52 libavformat-unstripped-52 libavutil-unstripped-49 libpostproc-unstripped-51 libswscale-unstripped-0 ffmpeg
```
Save the following as walkman.sh:
```
#!/bin/bash

ffmpeg -i $1 -an -pass 1 -s 320x240 -vcodec libx264 -b 512k -flags +loop -cmp +chroma -partitions 0 -me_method dia -subq 1 -trellis 0 -refs 1 -coder 0 -me_range 16 -g 250 -keyint_min 25 -sc_threshold 40 -i_qfactor 0.71 -bt 512k -maxrate 768k -bufsize 2M -qcomp 0.6 -qmin 10 -qmax 51 -qdiff 4 -level 13 -threads 0 -f mp4 /dev/null

ffmpeg -i $1 -acodec libfaac -ab 96k -pass 2 -s 320x240 -vcodec libx264 -b 512k -flags +loop -cmp +chroma -partitions +parti4x4+partp8x8+partb8x8 -flags2 +mixed_refs -me_method umh -subq 6 -trellis 1 -refs 5 -coder 0 -me_range 16 -g 250 -keyint_min 25 -sc_threshold 40 -i_qfactor 0.71 -bt 512k -maxrate 768k -bufsize 2M -qcomp 0.6 -qmin 10 -qmax 51 -qdiff 4 -level 13 -threads 0 -f mp4 $2
```
Make the script executable:
```
chmod +x walkman.sh
```
Run the script:
```
./walkman.sh inputfile.avi output.mp4
```
If your player doesn't like it, then run output.mp4 through MP4Box and try to play it in the Walkman.  Get MP4Box (it's part of gpac package):
```
sudo apt-get install gpac
```
Run it:
```
MP4Box -add output.mp4 newoutput.mp4
```

---

### Post by djbushido on 2008-11-16
looks good, but how do i make ffmpeg do 1 pass? I don't usually have the time for 2-pass encoding...

EDIT: the Walkman script works, i built my version of ffmpeg against the libx264 from git repo, so i now have videos for my Walkman!!!
Also, not marking solved just yet, because i don't know how to have ffmpeg just do 1 pass encoding...

---

### Post by FakeOutdoorsman on 2008-11-16
Robert Swain's [iPod video guide](http://rob.opendot.cl/index.php/useful-stuff/ipod-video-guide/) has some one-pass examples.

---

### Post by djbushido on 2008-11-17
cool! thanks for the guide, used it to create a 1-pass script for my walkman. I'll post the script later, so anyone can use it.

EDIT: this script can be used for converting videos for use with the Sony Walkman NWZ-A728 series of players. You must have ffmpeg built against libx264 version .65 or higher. The usage is: ./walkman-1pass.sh <input.whatever> <output.mp4>
The input video CAN NOT have any spaces in the name. This is just ffmpeg. The video is converted to 320x240. I think that is about it, if anyone has questions, feel free to reply or PM me.
```
ffmpeg -i $1 -acodec libfaac -ab 128k -s 320x240 -vcodec libx264 -b 500k -flags +loop -cmp +chroma -partitions +parti4x4+partp8x8+partb8x8 -flags2 +mixed_refs -me_method umh -subq 6 -trellis 1 -refs 5 -coder 0 -me_range 16 -g 250 -keyint_min 25 -sc_threshold 40 -i_qfactor 0.71 -bt 500k -maxrate 768k -bufsize 2M -qcomp 0.6 -qmin 10 -qmax 51 -qdiff 4 -level 13 -title $2 -threads 0 -f mp4 $2
```

---

### Post by Keyper7 on 2008-11-18
I think quotation marks can solve the spaces problem.

---

### Post by djbushido on 2008-11-18
There's a thought... I'll try that later and post the results.

---

### Post by 3rdalbum on 2008-11-18
It's like a little slice of yesteryear :-)

About a year ago, I released a GUI program that will encode video files for the Walkman. I've improved it since then:

[https://launchpad.net/blacklight/+download]("https://launchpad.net/blacklight/+download")

Download the first and second items on the list (the backend and the GUI). Install them both. In Synaptic Package Manager, go to Blacklight and right-click it, and then mark all the "suggests" packages for installation too if they aren't already installed (or if you haven't already built your own ffmpeg).

This program reduces video encoding to either a quick command or a couple of mouse-clicks. Oh, and unlike mencoder it will use as many cores as it can, if you give it multiple files.

---

### Post by octoberdan on 2008-12-27
Thank you, that tool helped me out enormously! You should add a feature that warns you when syncing fails because of file permissions, or try to sudo in those situations. I've had no luck with the GUI as it just loops me through providing a password and selecting a mount, but the command line version works like a charm!

---

### Post by vinx on 2009-05-06
For 9.04 the version-numbers are little different. So search for "unstripped" in Synaptic, where you find the 5 needed libXXX-unstripped together, just between gstreamerXXX and libcfitsio3-dbg. Also install ffmpeg en libx264 and you're set.

---

