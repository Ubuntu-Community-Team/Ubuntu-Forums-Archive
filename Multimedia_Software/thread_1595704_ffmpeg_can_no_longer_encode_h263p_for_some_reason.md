---
title: "ffmpeg can no longer encode h263p for some reason"
date: 2010-10-13
forum: Multimedia Software
---

### Post by oopsie on 2010-10-13
Hi!

I recently installed Ubuntu 10.10 after using 10.04. While using 10.04 I used ffmpeg quite a bit and just a few days ago I was using ffmpeg to encode video with the h263p codec.

Anyway, for some reason ffmpeg no longer seems to want to decode h263p anymore. If I type "ffmpeg -codecs" to get a codec list, I get

"  EV    h263p           H.263+ / H.263-1998 / H.263 version 2"

When it used to be "DEV" for decode / encode video. But now just " EV"

Even on the ffmpeg website here [http://ffmpeg.org/general.html#SEC3](http://ffmpeg.org/general.html#SEC3) it says ffmpeg should still be able to decode h263p. Yet, it can't!

I've tried installing all sorts of codec libraries and I even followed a guide to download and compile ffmpeg myself. Nothing seems to change.

Does anybody have any idea what's going on? Being unable to play these videos I'm encoding, kinda makes what I'm doing pointless =S

Any help would be appreciated.

---

### Post by andrew.46 on 2010-10-13
Hi oopsie,

At the bottom of *ffmpeg -codecs* you should see the following note:

> 

Note, the names of encoders and decoders do not always match, so there are
several cases where the above table shows encoder only or decoder only entries
even though both encoding and decoding are supported. For example, the h263
decoder corresponds to the h263 and h263p encoders, for file formats it is even
worse.


Andrew

---

### Post by oopsie on 2010-10-14
That doesn't explain how I could play h263p videos a week ago using ubuntu 10.04, and can't now play them now with 10.10.

---

### Post by andrew.46 on 2010-10-14
Hi oopsie,

> **oopsie said:**
> That doesn't explain how I could play h263p videos a week ago using ubuntu 10.04, and can't now play them now with 10.10.

I was trying to create an h263p sample and found that FFmpeg will only put in into an mkv container. What container do you normally use? I would have expected 3gp...

Andrew

---

### Post by oopsie on 2010-10-14
Thank you for replying!!! Well I didn't know that it only supported mkv, but I was using mkv anyway :P

Do you have a file that you can link to me that you know 100% ffmpeg will turn into h263p for you?

And give the command you use with ffmpeg? Just so I can confirm 100% that it's a computer problem and not a me being stupid problem.

---

### Post by andrew.46 on 2010-10-14
Hi oopsie,

> **oopsie said:**
> Thank you for replying!!! Well I didn't know that it only supported mkv, but I was using mkv anyway :P

I have been hoping that somebody with great knowledge of h263p would turn up and make all of this clear, but we appear to be on our own here :(.


> Do you have a file that you can link to me that you know 100% ffmpeg will turn into h263p for you?

And give the command you use with ffmpeg? Just so I can confirm 100% that it's a computer problem and not a me being stupid problem.

Well it actually turned out to be something of a struggle but if you have a look in:

[http://www.andrews-corner.org/tmp/](http://www.andrews-corner.org/tmp/)

you will see the file guardians.mov, which is the source file, and guardians_h263.mkv which is the output file, I will leave them there for a couple of days. The rather tortured commandline I used is as follows:

```

ffmpeg -y -ss 06 -i guardians.mov -itsoffset 00:00:00.850 \
       -ss 06 -i guardians.mov -map 1.0 -map 0.1 \
       -vcodec h263p -b 900k -acodec libfaac -ab 128k  \
      -vf scale=352:148,pad=352:288:0:70:black \
       guardians_h263.mkv

```

I did not realise that h263 was such a pain to work with! I fixed a rather nasty AV desync with *-itsoffset* but the biggest puzzle was that unless the resulting file agreed with conventional h263 sizes many players would not play it at all. I thought h264p liberated you from this problem? Anyway all the crazy scaling and padding left the output file a conventional h263 size which played with SMPlayer and vlc and does not look too horrible, but the high bitrate is a little against the spirit of h263...

Have a look at both files, I am sure you could produce a better result, I suspect you will need the latest svn FFmpeg to use the video filters I have used. If you have not seen it already the best guide for building this is here:

HOWTO: Install and use the latest FFmpeg and x264
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

All the best,

Andrew

---

### Post by oopsie on 2010-10-15
Bingo!

Problem found! But not solved

For some reason the latest ffmpeg that comes with ubuntu 10.10 cannot decode h263p at unusual sizes when I know absolutely 100% that it could in 10.04. I know because I was making some really tiny video files at a resolution of 160x120 or even lower a couple of weeks ago, and they played fine!

Hell, I just rebooted into a 10.04 live CD and encoded a h263p video at a stupid resolution of 120x48 just to test, and it worked. Just using the simple command "ffmpeg -i randomvideofile -vcodec h263p -s 160x48 -an blah.mkv" or something along those lines.

I used ffplay and it worked fine on the 10.04 live CD. But on 10.10, ffplay comes up with the error "[h263 @ 0x20c6b80]header damaged"

So it looks like ffmpeg has changed, or got a bug or something.

I don't suppose you know how I can install the older ubuntu 10.04 version of ffmpeg?

---

### Post by andrew.46 on 2010-10-15
Hi oopsie,

Well I can certainly confirm this problem with the svn FFmpeg. If an attempt is made to create a file using *h263p* outside the normal size constraints imposed by *h263* encoding the files will be unplayable with 'damaged header' messages from FFplay at least.

There would be a good case for a bug report to the FFmpeg developers but it would be nice to pinpoint the change that has done this damage. Hmmmm.... time to call in the cavalry...

Andrew

---

### Post by andrew.46 on 2010-10-20
Looks like the cavalry is caught up in his real life :(. I have posted to FFmpeg users and hopefully this will bring some resolution to the issue, at least for the svn FFmpeg:

h263p encoding produces unplayable files: damaged headers
[http://lists.mplayerhq.hu/pipermail/ffmpeg-user/2010-October/027591.html](http://lists.mplayerhq.hu/pipermail/ffmpeg-user/2010-October/027591.html)

**Edit:** Wooo hoooo! The issue is completely resolved in svn and works perfectly on my setup. I would strongly advise you install the svn:

HOWTO: Install and use the latest FFmpeg and x264
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

to benefit from this fix and countless other fixes and improvements :).

Andrew

---

