---
title: "Videos recorded on Android phone don't play"
date: 2013-02-02
forum: Multimedia Software
---

### Post by Beacon11 on 2013-02-02
Hello all.

My Motorola RAZR MAXX records videos with a .mp4 extension. According to this page ([http://developer.android.com/guide/appendix/media-formats.html](http://developer.android.com/guide/appendix/media-formats.html)) that seems to be H.264 AVC. I can't for the life of me get VLC or totem to play these files-- VLC does nothing, and totem says "could not determine type of stream."

I have installed restricted-extras, still no go. Google isn't really helping me either... this is frustrating. I would really appreciate some help!

---

### Post by Beacon11 on 2013-02-02
Note:

```
$ ffmpeg -i 2013-02-01_18-29-25_11.mp4 
ffmpeg version 0.8.5-4:0.8.5-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Jan 24 2013 18:01:36 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
2013-02-01_18-29-25_11.mp4: Invalid data found when processing input
```

This video plays fine on my phone!

---

### Post by ron999 on 2013-02-02
> **Beacon11 said:**
> Hello all.

My Motorola RAZR MAXX records videos with a .mp4 extension... I would really appreciate some help!
Use MediaInfo to investigate these videos, or upload a sample somewhere.

---

### Post by Beacon11 on 2013-02-02
> **ron999 said:**
> Use MediaInfo to investigate these videos, or upload a sample somewhere.

I've never used MediaInfo before... I installed the gui and tried to enable all options. This is the best I could get:

> General
Count                                    : 278
Count of stream of this kind             : 1
Kind of stream                           : General
Kind of stream                           : General
Stream identifier                        : 0
Inform                                   : 3.95 MiB
Complete name                            : /home/krf/Desktop/phone_test.mp4
Folder name                              : /home/krf/Desktop
File name                                : phone_test
File extension                           : mp4
File size                                : 4141056
File size                                : 3.95 MiB
File size                                : 4 MiB
File size                                : 3.9 MiB
File size                                : 3.95 MiB
File size                                : 3.949 MiB
Stream size                              : 4141056
Stream size                              : 3.95 MiB (100%)
Stream size                              : 4 MiB
Stream size                              : 3.9 MiB
Stream size                              : 3.95 MiB
Stream size                              : 3.949 MiB
Stream size                              : 3.95 MiB (100%)
Proportion of this stream                : 1.00000
File last modification date              : UTC 2013-02-02 15:33:36
File last modification date (local)      : 2013-02-02 10:33:36

I also uploaded a sample here: [http://cloud.rainveiltech.com/public.php?service=files&t=18210a9da64a63ce3921a19d0a4aee03](http://cloud.rainveiltech.com/public.php?service=files&t=18210a9da64a63ce3921a19d0a4aee03)

Thank you very much for your help... this is definitely not my area of expertise :) .

---

### Post by ron999 on 2013-02-02
I can't play **phone_test.mp4** either. :(

---

### Post by Beacon11 on 2013-02-02
> **ron999 said:**
> I can't play **phone_test.mp4** either. :(

Argh!

The only platform on which I've been able to play that file is my phone. I can't get it to work in Ubuntu, Windows, or my old mac (although that was still only using VLC or Quicktime). I have GOT to be missing something... how do OTHER people do this? Every video I record on my phone works this way!

---

### Post by Beacon11 on 2013-02-02
Wait... I have an idea. My phone is encrypted. I've been pulling video files off of the SD card. Perhaps therein lies the problem...

---

### Post by Beacon11 on 2013-02-02
> **Beacon11 said:**
> Wait... I have an idea. My phone is encrypted. I've been pulling video files off of the SD card. Perhaps therein lies the problem...

Well... I was able to upload to YouTube...

---

### Post by Beacon11 on 2013-02-02
> **Beacon11 said:**
> Wait... I have an idea. My phone is encrypted. I've been pulling video files off of the SD card. Perhaps therein lies the problem...

This is indeed the problem-- as soon as I turned off SD card encryption this worked. Now I just need to figure out how to decrypt the video I've already taken! It seems that files will be decrypted for off-device transfer as long as you use device software (i.e. don't access the SD card directly). I'm testing with Ubuntu One Files for Android now.

EDIT: Bingo. Put it in Ubuntu One and it's decrypted. Painful lesson.

Thanks for your help ron999; I didn't think of this, and I'm afraid I wasted your time. I hope you have a lovely weekend!

---

