---
title: "Help with Pitivi video editor and youtube"
date: 2010-05-14
forum: Multimedia Software
---

### Post by Crazy K on 2010-05-14
I recently purchased a Creative Vado 3rd Gen Pocket Cam. Anyways I took some video of my niece's spring concert, but I took 3 separate videos. I figured out how to connect them together and make one video in Pitivi. Thing is, I can't upload it to youtube. The 3 videos together make up around 9 minutes. I know they support MP4 format, but Idk what to do during the rendering process in Pitivi to make it a true MP4 format. 

I just need to know what to choose under: 

Container
Audo Codec
Video Codec 

and if I need to do anything to the settings. Each video was taken in 720p. 

Anyways hope you guys can help me figure this out, because I'd like to upload it to youtube to share with the family.

I figured it out. Sorry for the bother. ;)

---

### Post by dberg on 2010-05-21
Could you perhaps post what you did to get it working?

I'm not sure if you were having the same problem that I am, but whenever I make a video in Pitivi and try to upload it, it ends up with working audio but jumbled video.

---

### Post by freedomisok on 2010-05-23
Ok, same problem to me!

I made a video with PITIVI, uploaded on youtube: audio is fine but the video is just a lot of confused colors...

I need to know wich encoding setting youtube wants... can someone help me?

thank you very much guys...

---

### Post by dberg on 2010-05-28
Just thought I'd update that I finally found a combination that seems to make a video file that is playable on Youtube.

Container: FLV muxer [flvmux]
Audio Codec: L.A.M.E. mp3 encoder [lamemp3enc]
Video Codec: FFmpeg Flash Video (FLV) encoder [ffenc_flv]


Probably not the ideal settings, but at least Youtube doesn't choke on it.

---

### Post by asktoby on 2010-09-02
I don't have lame available but was able to get video and sound using
Container: Avi muxer [avimux]
FFmpeg Window Media Audio 2 encoder [ffenc_wmav2]
JPEG image encoder [jpegenc]

---

### Post by asktoby on 2010-09-02
Another that works:

Container: FLV muxer [flvmux]
Audio: FFmpeg ADPCM Shockwave Flash encoder [ffenc_adpcm_swf]
Video: FFmpeg Flash Video (FLV) encoder [ffenc_flv]

---

### Post by anspideog on 2010-10-21
> **asktoby said:**
> Another that works:

Container: FLV muxer [flvmux]
Audio: FFmpeg ADPCM Shockwave Flash encoder [ffenc_adpcm_swf]
Video: FFmpeg Flash Video (FLV) encoder [ffenc_flv]


This worked for me. Thanks a million!

---

### Post by Jaymoid on 2010-10-29
> **asktoby said:**
> I don't have lame available but was able to get video and sound using
Container: Avi muxer [avimux]
FFmpeg Window Media Audio 2 encoder [ffenc_wmav2]
JPEG image encoder [jpegenc]

Hmm the others didn't but that worked for me! Thanks

---

### Post by flitbee on 2010-12-05
> **dberg said:**
> Just thought I'd update that I finally found a combination that seems to make a video file that is playable on Youtube.

Container: FLV muxer [flvmux]
Audio Codec: L.A.M.E. mp3 encoder [lamemp3enc]
Video Codec: FFmpeg Flash Video (FLV) encoder [ffenc_flv]


Probably not the ideal settings, but at least Youtube doesn't choke on it.

How'd you get these in your codec lists? I seem to have only 2. Ogg Theora and Ogg Vorbis. A video encoded in Ogg Theora doesn't show up in youtube. Some do, while some don't. I don't know why :(

---

### Post by asktoby on 2010-12-06
Have you got the codec packs installed? (good, bad, ugly...)

---

### Post by Grams79 on 2010-12-31
> **dberg said:**
> Just thought I'd update that I finally found a combination that seems to make a video file that is playable on Youtube.

Container: FLV muxer [flvmux]
Audio Codec: L.A.M.E. mp3 encoder [lamemp3enc]
Video Codec: FFmpeg Flash Video (FLV) encoder [ffenc_flv]

Probably not the ideal settings, but at least Youtube doesn't choke on it.

Worked great thanks!
I'm surprised that Youtube being Linux doesn't accept OGV.

---

### Post by Grams79 on 2011-01-13
> **flitbee said:**
> How'd you get these in your codec lists? I seem to have only 2. Ogg Theora and Ogg Vorbis. A video encoded in Ogg Theora doesn't show up in youtube. Some do, while some don't. I don't know why :(

Go to your **Ubuntu Software Center** and install **Restricted Extras**.
:popcorn:

---

### Post by flitbee on 2011-02-27
> **flitbee said:**
> How'd you get these in your codec lists? I seem to have only 2. Ogg Theora and Ogg Vorbis. A video encoded in Ogg Theora doesn't show up in youtube. Some do, while some don't. I don't know why :(

Whenw ill youtube start supporting Ogg Theor? It gives the best bang for buck (quality v/s size). AVI - takes up too much of space, its not practical.Haven't found the best combo yet..

---

### Post by antoniscy on 2011-04-01
I had success using these format settings: Video output: 720p HD (29,97 fps)
 Audio output: cd
 Export: WebM muxer [webmmux]
Uploaded to youtube and it runs great with good quality video (much better than flv or mp4)
.webm is a good open source format. (Check my video on [http://www.youtube.com/watch?v=CYCFSXjeXa8](http://www.youtube.com/watch?v=CYCFSXjeXa8) )

---

### Post by brad1138 on 2011-05-05
> **Grams79 said:**
> Go to your **Ubuntu Software Center** and install **Restricted Extras**.
:popcorn:


Hello, Just found this thread. I installed Restricted Extras, but Pitivi still only shows the same 5 options for video encoding:

Dirac
Smoke video
Theora
ON2 vp8
Dirac (again)

I restarted the comp, but that didn't help. 

What am I missing?

Thanks,
Brad

---

### Post by nolo on 2011-06-06
In case you haven't already figured this one out, you must choose a different "container" to show other video codecs.  The ones you see are compatible with the oggmux container.

Nolo

---

### Post by tapin13 on 2011-06-19
first of all: [http://www.google.com/support/youtube/bin/answer.py?answer=55744](http://www.google.com/support/youtube/bin/answer.py?answer=55744)

    WebM files - Vp8 video codec and Vorbis Audio codecs
    .MPEG4, 3GPP and MOV files - Typically supporting h264, mpeg4 video codecs, and AAC audio codec
    .AVI - Many cameras output this format - typically the video codec is MJPEG and audio is PCM
    .MPEGPS - Typically supporting MPEG2 video codec and MP2 audio
    .WMV
    .FLV - Adobe-FLV1 video codec, MP3 audio


I was used MPEGPS - Typically supporting MPEG2 video codec and MP2 audio, and it's uploaded ok!
PiTiVi 1.4!

---

### Post by quimkaos on 2011-06-19
> **brad1138 said:**
> I restarted the comp, but that didn't help. 

rarely that helps in Linux... it only helps when you can not (or know not) how to restart some service inside Ubuntu, or don't even know what service you need to restart... in Linux you only have to reboot your system when changes to kernel have been made (drivers integration, kernel upgrades/optimizations.... etc), not in something like this... in the case you had to restart a service you didn’t knew what it was you could simply log off and log in again....

---

