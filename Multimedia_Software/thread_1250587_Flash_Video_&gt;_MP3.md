---
title: "Flash Video &gt; MP3"
date: 2009-08-26
forum: Multimedia Software
---

### Post by jesuisbenjamin on 2009-08-26
Hello there,

I have some flash video and would like to convert it into an audio file, especially mp3.
How can i go about this? Which program should i use?

Thanks

---

### Post by magnus0 on 2009-08-26
```
ffmpeg -i flash_file.flv -ab 128k output.mp3
```

---

### Post by FakeOutdoorsman on 2009-08-26
If the Flash video contains MP3 audio you can just copy the stream and avoid re-encoding.  This will preserve the quality:
```
ffmpeg -i input.flv -acodec copy output.mp3
```
You can see if your flv contains mp3 audio with:
```
ffmpeg -i input.flv
```

---

### Post by scratman on 2009-08-26
Go to [http://code.google.com/p/winff/wiki/UbuntuInstallation]("http://code.google.com/p/winff/wiki/UbuntuInstallation") and download the .deb from there.  It has support for many audio and video formats, a nice friendly gui, and is lightning fast.

---

### Post by jesuisbenjamin on 2009-08-26
Hello guys,

Thanks for these amazing replies. 
Yet little problem occured:

```
[flv @ 0xb7ef94c8]Unsupported video codec (7)

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 25.00 (25/1)
Input #0, flv, from 'test.flv':
  Duration: 00:07:41.8, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: 0x0007, 25.00 tb(r)
    Stream #0.1: Audio: 0x000a, 44100 Hz, stereo
WARNING: The bitrate parameter is set too low. It takes bits/s as argument, not kbits/s
Output #0, mp2, to 'hallucinogen.mp3':
    Stream #0.0: Audio: mp2, 44100 Hz, stereo, 0 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
Unsupported codec (id=0) for input stream #0.1

```

What to do?
I follow your instructions but enjoy knowing what i am doing please explain if possible?
Cheers.

---

### Post by jesuisbenjamin on 2009-08-26
Looking into file properties i read: 

Type: Flash video (video/x-flv)
Codec: H.264/AVC Video

Among other things.

---

### Post by psychok9 on 2009-08-26
Try to downloand HQ version and open it later with avidemux.
Select the mp3 audio codec from the left bar and "Save audio" from menu... :)

---

### Post by jesuisbenjamin on 2009-08-27
Ok i managed to fix the issue thanks to this post: [http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)
Following instructions till step 4.

Thanks guys! :)

---

