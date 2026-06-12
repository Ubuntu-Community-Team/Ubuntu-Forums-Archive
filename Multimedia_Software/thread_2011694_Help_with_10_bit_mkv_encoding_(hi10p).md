---
title: "Help with 10 bit mkv encoding (hi10p)"
date: 2012-06-27
forum: Multimedia Software
---

### Post by christopher.suttles on 2012-06-27
I recently did a clean install of Ubuntu 12.04 on RAID 0 on my Asus laptop.

I currently have everything running great - even my 10 bit video playback in gnome mplayer plays just fine on my old core 2 duo.

No I have what is probably going to be a stupid question. I used to use megui in windows to encode videos to hi10p mkv's to save some space with my videos.

Is there a similar program that uses a GUI in linux? I have done a lot of googling for the past hour but everything I have found related to using ffmpeg and using shell.

Any help would be greatly appreciated!!

(P.S. I have handbrake installed and I know I can convert 10 bit to 8 bit, but I see no settings for 10 bit encoding and because the x264 is built into handbrake I can't simply replace the files)

---

### Post by andrew.46 on 2012-06-27
Problem would be that x264 can be compiled for either 10bit *or* 8bit:

```

  --bit-depth=BIT_DEPTH    set output bit depth (8-10) [8]

```

You can see that the default is actually 8bit. I guess you could experiment with rebuilding your copy of x264 for 10bit and see how the various guis react. Using FFmpeg or indeed x264 directly would probably be easier though....

---

