---
title: "COnvert video to 3GP fails"
date: 2013-03-09
forum: Multimedia Software
---

### Post by linuxyogi on 2013-03-09
I am trying to convert a flv video to 3gp with mobile media converter.

But I am getting this error



```
>> Command executed:
ffmpeg -y -i "/home/tux/325 litre Malawi cichlid tank - YouTube.flv"  -vf scale=352:288 -f 3gp -vcodec h263 -r 15 -b 200k -acodec libvo_aacenc -ac 2 -ar 32000 -ab 64k "/home/tux/325 litre Malawi cichlid tank - YouTube.3gp"


>> Result: 
ffmpeg version 0.8.5-4:0.8.5-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Jan 24 2013 18:01:36 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
[flv @ 0x11bd9c0] Estimating duration from bitrate, this may be inaccurate
Input #0, flv, from '/home/tux/325 litre Malawi cichlid tank - YouTube.flv':
  Metadata:
    starttime       : 0
    totalduration   : 224
    totaldatarate   : 1262
    bytelength      : 35310013
    canseekontime   : true
    sourcedata      : B4A7DA925MM1362765817125709
    purl            : 
    pmsg            : 
  Duration: 00:03:43.80, start: 0.000000, bitrate: 1284 kb/s
    Stream #0.0: Video: h264 (Main), yuv420p, 854x478 [PAR 1:1 DAR 427:239], 1185 kb/s, 25 tbr, 1k tbn, 50 tbc
    Stream #0.1: Audio: aac, 44100 Hz, stereo, s16, 98 kb/s
[buffer @ 0x11bd940] w:854 h:478 pixfmt:yuv420p
[scale @ 0x11c04a0] w:854 h:478 fmt:yuv420p -> w:352 h:288 fmt:yuv420p flags:0x4
[h263 @ 0x1415140] Invalid pixel aspect ratio 3843/2629, limit is 255/255
Output #0, 3gp, to '/home/tux/325 litre Malawi cichlid tank - YouTube.3gp':
    Stream #0.0: Video: h263, yuv420p, 352x288 [PAR 3843:2629 DAR 427:239], q=2-31, 200 kb/s, 90k tbn, 15 tbc
    Stream #0.1: Audio: libfaac, 32000 Hz, stereo, s16, 200 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Error while opening encoder for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height
----------------------------

```

---

### Post by Merrattic on 2013-03-10
There seems to be something wrong with "h263". The same (similar) command run with "h264" works fine?
(I am using the compiled version of "real" ffmpeg, dated Sep 2012)


Member FODM to the rescue please ?

---

### Post by andrew.46 on 2013-03-10
Perhaps try *-r 25* for your commandline instead of *-r 15*.

---

### Post by Merrattic on 2013-03-10
I tried with -r 15 and that works! :)

```
ffmpeg -i test.mp4 -c:v h263 -r 15 -b:v 200k -vf scale=352:288 -aspect 16:9 -c:a libopencore_amrnb -ac 1 -ar 8000 -b:a 12200 test.3gp
```

In fact the least I could get away with to make it run was:

```
ffmpeg -i test.mp4 -vf scale=352:288 -ac 1 -ar 8000 -b:a 12200 test1.3gp
```

---

### Post by linuxyogi on 2013-03-11
```
~$ ffmpeg -i malawi.flv -c:v h263 -r 15 -b:v 200k -vf scale=352:288 -aspect 16:9 -c:a libopencore_amrnb -ac 1 -ar 8000 -b:a 12200 test.3gp
ffmpeg version 0.8.5-4:0.8.5-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Jan 24 2013 18:01:36 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
[flv @ 0x17089c0] Estimating duration from bitrate, this may be inaccurate
Input #0, flv, from 'malawi.flv':
  Metadata:
    starttime       : 0
    totalduration   : 224
    totaldatarate   : 1262
    bytelength      : 35310013
    canseekontime   : true
    sourcedata      : B4A7DA925MM1362765817125709
    purl            : 
    pmsg            : 
  Duration: 00:03:43.80, start: 0.000000, bitrate: 1284 kb/s
    Stream #0.0: Video: h264 (Main), yuv420p, 854x478 [PAR 1:1 DAR 427:239], 1185 kb/s, 25 tbr, 1k tbn, 50 tbc
    Stream #0.1: Audio: aac, 44100 Hz, stereo, s16, 98 kb/s
Unrecognized option 'c:v'
Failed to set value 'h263' for option 'c:v'








```


```

~$ ffmpeg -i malawi.flv -c:v h263 -r 25 -b:v 200k -vf scale=352:288 -aspect 16:9 -c:a libopencore_amrnb -ac 1 -ar 8000 -b:a 12200 test.3gp
ffmpeg version 0.8.5-4:0.8.5-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Jan 24 2013 18:01:36 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
[flv @ 0x11e79c0] Estimating duration from bitrate, this may be inaccurate
Input #0, flv, from 'malawi.flv':
  Metadata:
    starttime       : 0
    totalduration   : 224
    totaldatarate   : 1262
    bytelength      : 35310013
    canseekontime   : true
    sourcedata      : B4A7DA925MM1362765817125709
    purl            : 
    pmsg            : 
  Duration: 00:03:43.80, start: 0.000000, bitrate: 1284 kb/s
    Stream #0.0: Video: h264 (Main), yuv420p, 854x478 [PAR 1:1 DAR 427:239], 1185 kb/s, 25 tbr, 1k tbn, 50 tbc
    Stream #0.1: Audio: aac, 44100 Hz, stereo, s16, 98 kb/s
Unrecognized option 'c:v'
Failed to set value 'h263' for option 'c:v'

```

---

### Post by andrew.46 on 2013-03-11
You have an aged version of FFmpeg :). Try using the older *-acodec* and* -vcodec *syntax...

---

### Post by FakeOutdoorsman on 2013-03-11
This is confirmed as Yet Another Libav Bug (YALB). It will work if you use a recent real ffmpeg as shown by Merrattic. The difference is that the [fake so-called ffmpeg from libav](http://stackoverflow.com/a/9477756/1109017) (and their current code) will just fail with the "Invalid pixel aspect ratio" message, but real ffmpeg will automatically reduce the ratio limit and continue to encoding. You can download a [static build of ffmpeg](http://ffmpeg.org/download.html#LinuxBuilds). No need to install ([example instructions](http://ubuntuforums.org/showthread.php?t=2121268&p=12536453&viewfull=1#post12536453)), or you can [compile ffmpeg](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide) if you like.

We can also improve it a bit since forcing the scale will probably stretch it vertically, so you can add some padding with the [pad filter](http://ffmpeg.org/ffmpeg-filters.html#pad).
```
ffmpeg -i input -vf "scale=352:-1,pad=iw:288:0:trunc((288-ih)/2)" -vcodec h263 -b:v 200k -acodec libvo_aacenc -ab 128k output.3gp
```
The "trunc((288-ih)/2)" is just a fancy way of saying 45 since 288 (the desired height) - 197 (the value *-1* in the scale filter gives you) = 91 and 91 / 2 = 45.5, so it has to be rounded up or down for the pad to work.

Valid sizes for this encoder are 128x96, 176x144, 352x288, 704x576, and 1408x1152.

---

### Post by linuxyogi on 2013-03-12
[https://launchpad.net/~jon-severinsson/+archive/ffmpeg](https://launchpad.net/~jon-severinsson/+archive/ffmpeg)

I just updates ffmpeg. Now it encodes. 

And my phone can play the videos too. 

Thanks for all your replies.

---

### Post by andrew.46 on 2013-03-12
Good to hear that you have resolved the issue :).

---

