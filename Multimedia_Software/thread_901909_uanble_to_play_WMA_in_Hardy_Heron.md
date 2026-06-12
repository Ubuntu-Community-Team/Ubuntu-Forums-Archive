---
title: "uanble to play WMA in Hardy Heron"
date: 2008-08-26
forum: Multimedia Software
---

### Post by riotculture on 2008-08-26
I am quite new to Ubuntu. I installed Ubuntu 8.04 last week and am  really falling in love with it and the open source community. 

I do unfortunately have a quite large WMA selection. I believe I have installed all the right plug ins.

When I  gst-inspect-0.10 |grep wmasf:  rtspwms: WMS RTSP Extension
I get the output.

ffmpeg:  ffdec_wmav2: FFMPEG Windows Media Audio v8/9 decoder
ffmpeg:  ffdec_wmav1: FFMPEG Windows Media Audio v7 decoder
ffmpeg:  ffdec_wmv3: FFMPEG Windows Media Video v9 decoder
ffmpeg:  ffdec_wmv2: FFMPEG Windows Media Video v8 decoder
ffmpeg:  ffdec_wmv1: FFMPEG Windows Media Video v7 decoder
ffmpeg:  ffenc_wmav2: FFMPEG Windows Media Audio v8/9 encoder
ffmpeg:  ffenc_wmav1: FFMPEG Windows Media Audio v7 encoder
ffmpeg:  ffenc_wmv2: FFMPEG Windows Media Video v8 encoder
ffmpeg:  ffenc_wmv1: FFMPEG Windows Media Video v7 encoder
typefindfunctions: video/x-ms-asf: asf, wm, wma, wmv

Still I cant play WMA in any application.

VLC:
the scroll is running but there is no sound.

When I open in terminal it says:

[00000312] main decoder error: no suitable decoder module for fourcc `wmal'.
VLC probably does not support this sound or video format.


Amarok:
Will import the files, but when I try to play them i get:
Error loading media
There is no available decoder.


Rhythmbox:
Will not import states under Import Errror:
The GStreamer plugins to decode "Unknonwn" files cannot be found.

When I run in terminal it says:

Rhythmbox-Message: Missing plugin: gstreamer|0.10|rhythmbox-metadata|audio/x-asf-unknown decoder|decoder-audio/x-asf-unknown, codec_id=(int)355
no application found
Rhythmbox-Message: No installation candidate for missing plugins found.

I have followed the steps in [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
with no results.

I have searched the forum for a solution on this. I do not believe the files are DRM, but I am not 100% sure. Is there a way to check this?

I would be very grateful on any help on how i can be able to play my WMA files in Ubuntu (and I will make sure to never rip anything in WMA again).

I am sorry if the post is a bit long, I just wanted to add all the info that i as a Ubuntu novice think might be useful.
PS. I run AMD64 if that matters.

---

### Post by tuxxy on 2008-08-26
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by mrsteveman1 on 2008-08-26
There are multiple codec libraries in Linux (grrrr), like xine, gstreamer, etc.

I think some apps use different ones, so while you may have ffmpeg installed it may not be being used for some apps.

---

### Post by riotculture on 2008-08-27
Thanks to both of you for fast answering. My love for open source and the community working with it is high and rising.

I have already installed the restricted formats. I also have gxine and amarok-exine already installed. I think the multiple codecs libraries may be the key to my problems. 
 
How to search for problem and solve?

---

### Post by mc4man on 2008-08-27
If you didn't get it all squared away yet then install w32codecs.
available by adding medibuntu to software sources, see here for how

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

or directly from here (choose .deb from 18-july........

[http://packages.medibuntu.org/pool/non-free/w/w32codecs/](http://packages.medibuntu.org/pool/non-free/w/w32codecs/)

As far as players Amarok will play **all** wma's from normal to loseless (also the most configurable player, actually knows what autoplay means vs. autostart.
I'd add libxine1-ffmpeg if you install Amarok (available in synaptic

---

### Post by riotculture on 2008-09-03
Thanks everyone for the effort. Still I am unable to play wma. I have installed the restricted formats. I have followed the instructions on [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu). Still unable to play wma. Any hope. My Amarok is on xine by the way and I run on AMD64. Any ideas on how to solve this?

---

### Post by mc4man on 2008-09-03
> My Amarok is on xine by the way and I run on AMD64

Amarok can play 'normal' wma's by default. As far as wma pro and wma vbr I'm not sure. (meaning the default amarok). For **lossless** wma you'll need w32codecs installed for sure. The 64bit version of these codecs is pretty much worthless.

You may want to search and see if there's any way to use the 32 bit version of codecs on AMD64. (I believe there is

---

### Post by riotculture on 2008-09-08
> **mc4man said:**
>  For **lossless** wma you'll need w32codecs installed for sure. The 64bit version of these codecs is pretty much worthless.

You may want to search and see if there's any way to use the 32 bit version of codecs on AMD64. (I believe there is

Thanks, I guess I finally got the cause of my problem. I am a bit afraid to mess around with these codecs as I have reinstalled hardy heron five times in my first month of testing it. Is it anyone who knows about a "safe" and simple way to work around this and get a 32 bit player working on AMD 64?

(Preferably a player with library and playlist function)

---

### Post by riotculture on 2008-09-09
I sort of solved this problem by installing realplayer following this guide. 

[http://www.hightechsister.com/2008/09/how-to-play-wma-lossless-files-on-your-linux-box/](http://www.hightechsister.com/2008/09/how-to-play-wma-lossless-files-on-your-linux-box/)

So now my WMA's play on my 64 bit Hardy Heron system. Still I hope that the proper formats will be available in in the w64codecs, As I find amarok and rhythmbox to have a much nicer interface than realplayer.

---

### Post by Bucky Ball on 2008-09-09
Try in future saving your audio files as FLAC. Runs on all things linux and if you are compressing and decompressing, they are lossless (FLAC = Free Lossless Audio Codec). Cool, and there is codec for windoze to run 'em too. :)

---

### Post by riotculture on 2008-09-10
Certainly will. I will never anymore rip anything in WMA or other restricted formats. A big thank to the Ubuntu community and those who have answered me on this issue.

---

