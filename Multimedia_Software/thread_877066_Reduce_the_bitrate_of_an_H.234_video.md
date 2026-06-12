---
title: "Reduce the bitrate of an H.234 video?"
date: 2008-08-01
forum: Multimedia Software
---

### Post by SniperSlap on 2008-08-01
I just bought a new HD video camera and while I'm really pleased with it, the quality of the videos is too high for my 2GHz Core2 Duo to play them!

I'm alright with keeping the high quality videos, but I was wondering if there's any way to reduce the bitrate of the videos so that I can do things like upload them to google video or give them to others.

Or perhaps in the least -- play them!  LOL

So far, I've tried ffmpeg with the -b option, but it appears to only be making ~36MB files from a 300MB video!

I suspect that I'm perhaps missing another indicator in quality.  Is there anyone who can help me figure out a way to use the same MP4 video format, but simply tone it down a little?

---

### Post by timcredible on 2008-08-01
ffmpeg will do it, but it's difficult trying to read through and understand all the options, though, isn't it?  i know there's a bitrate parameter, but don't know what it is.  try winff as a front-end gui to ffmpeg, it makes it easier to work with ffmpeg.

---

### Post by theacoustician on 2008-08-01
> **SniperSlap said:**
> I just bought a new HD video camera and while I'm really pleased with it, the quality of the videos is too high for my 2GHz Core2 Duo to play them!

I'm alright with keeping the high quality videos, but I was wondering if there's any way to reduce the bitrate of the videos so that I can do things like upload them to google video or give them to others.

Or perhaps in the least -- play them!  LOL

So far, I've tried ffmpeg with the -b option, but it appears to only be making ~36MB files from a 300MB video!

I suspect that I'm perhaps missing another indicator in quality.  Is there anyone who can help me figure out a way to use the same MP4 video format, but simply tone it down a little?B frames won't help you play back the files, it'll only make it worse.  Most of the options you're enabling will only boost the CPU requirements for decoding (that's why the files are smaller at equal quality).  You have to think of it as "Quality, Size, Minimal Decoding Requirements : Pick Two".  If you want to make it easier to watch them, make the video all I-frame.  It'll be huge, but your PC won't have any problem playing them.  This is all assuming you mean H.264, not H.234.  H.234 is encryption key standards for videoconferencing, so ... yeah.

Easiest thing to do is fire up Avidemux and use some of the presets.  That way you can get rolling without having to learn all the switches in H.264.  I believe they even have a Youtube transcode setting.  Later on when you get more comfortable with the camera and the codec, you can delve into all the switches.

---

### Post by SniperSlap on 2008-08-02
> **theacoustician said:**
> B frames won't help you play back the files, it'll only make it worse.  Most of the options you're enabling will only boost the CPU requirements for decoding (that's why the files are smaller at equal quality).  You have to think of it as "Quality, Size, Minimal Decoding Requirements : Pick Two".  If you want to make it easier to watch them, make the video all I-frame.  It'll be huge, but your PC won't have any problem playing them.  This is all assuming you mean H.264, not H.234.  H.234 is encryption key standards for videoconferencing, so ... yeah.

Easiest thing to do is fire up Avidemux and use some of the presets.  That way you can get rolling without having to learn all the switches in H.264.  I believe they even have a Youtube transcode setting.  Later on when you get more comfortable with the camera and the codec, you can delve into all the switches.


Thank you so much for your help!  I must have been a bit tired while writing the original post, you are right in assuming the video standard.

I'm very familiar with formats and  balances between options, so I understand what you're saying 100%.  I guess my problem is that I'm only fluent in what I've encountered up until any given moment.  With a recent family purchase of a new video camera, I'm suddenly tasked with a ten week memorization assignment!

I've got avidemux installed and running now.

I wonder if there's a way to get google video to show movies at 16:9?  If you or anyone else can share more advice, I'm more than happy to hear it.

Take care!

---

### Post by theacoustician on 2008-08-04
> **SniperSlap said:**
> Thank you so much for your help!  I must have been a bit tired while writing the original post, you are right in assuming the video standard.

I'm very familiar with formats and  balances between options, so I understand what you're saying 100%.  I guess my problem is that I'm only fluent in what I've encountered up until any given moment.  With a recent family purchase of a new video camera, I'm suddenly tasked with a ten week memorization assignment!

I've got avidemux installed and running now.

I wonder if there's a way to get google video to show movies at 16:9?  If you or anyone else can share more advice, I'm more than happy to hear it.

Take care!There are only a few selected resolutions and encode types that Google allows to be uploaded to their service and retain 16:9 formatting.  I think they do this to help distinguish partner services from average joe uploads.  853x480 MPEG2 used to be one that worked, but it seems as if they're blocking all users now from true 16:9.  You can always letterbox to maintain aspect ratio, but that's a little ghetto.   Try blip.tv.  Their video quality is nicer and they allow 16:9.

---

