---
title: "How to convert invalid MP4 for playback on the PS3"
date: 2011-05-31
forum: Multimedia Software
---

### Post by mikeym on 2011-05-31
Hi,

I've just been searching in vain for a way of converting a MP4 I have that is *h264* video and *aac* audio, so that it will play properly on the PS3. 

It currently will play on the PS3 but at double frame-rate and without sound. Does anyone have any ideas. I'm not particularly wanting to re-encode the whole thing. 

Even advice as to how to demux the audio and video streams from the MP4 would be useful.

Thanks, 

Mikey

---

### Post by mikeym on 2011-05-31
Not much success with the demuxing. I've found little in the way of advice for how to handle MP4s, most online guides tend to focus on MKV to MP4 and use *mkvextract* to demux audio and video streams. (For examples see [here]("http://www.ode2.com/?p=11").)


I've had better success with transcoding (though it takes a bit longer). [This page]("http://www.prupert.co.uk/2009/10/10/how-to-use-ffmpeg-to-transcode-video-for-the-ps3/") has instructions for transcoding using *ffmpeg, libfaac and libx264* into PS3 compatible MP4 that worked for me. 

The second ffmpeg command on the page worked:

```

ffmpeg -y -i my_video_file -vcodec libx264 -level 41 -vpre normal -crf 24 -threads 0 -acodec libfaac -ab 128k -ac 2 -ar 48000 my_video_file_out.mp4

```

However I had to install the unrestricted video libraries from [medibuntu.org]("http://medibuntu.org/repository.php"). Follow the 2 sets of instructions on the page for Adding the repository then upgrade:

```

sudo apt-get upgrade

``` 

Would still like to know if anyone can do this without transcoding. The exact video MP4 I'm trying to make compatible is the MP4 files produced using *get-iplayer*.

---

### Post by ron999 on 2011-05-31
> **mikeym said:**
>  The exact video MP4 I'm trying to make compatible is the MP4 files produced using *get-iplayer*.

Hi

Sometimes those files from **get_iplayer** are available in different versions.
Have you tried the different ones with your PS3 ?

400x224
--mode=flashlow

640x360 (382Kbps - LOW BITRATE !)
--mode=flashstd

640x360 (704Kbps)
--mode=flashhigh (Not needed, because it's the default).

832x468
--mode=flashvhigh

1280x720
--mode=flashhd

---

