---
title: "ffmpeg error: non-existing PPS referenced"
date: 2011-11-21
forum: Multimedia Software
---

### Post by Chiel92 on 2011-11-21
Hi all,

I want to convert a flv file to mp3.
Normally it gives no problems, but with the current file i'm experiencing troubles.
I run this:
```
ffmpeg -i "test.flv" -acodec libmp3lame -ab 128k "test.mp3"

```and get these errors:
```

...more stuff like below...
[h264 @ 0xa010fa0]decode_slice_header error
[h264 @ 0xa010fa0]no frame!
[h264 @ 0xa010fa0]non-existing PPS referenced
[h264 @ 0xa010fa0]B picture before any references, skipping
[h264 @ 0xa010fa0]decode_slice_header error
[h264 @ 0xa010fa0]no frame!
[h264 @ 0xa010fa0]non-existing PPS referenced
[h264 @ 0xa010fa0]B picture before any references, skipping
[h264 @ 0xa010fa0]decode_slice_header error
[h264 @ 0xa010fa0]no frame!
[h264 @ 0xa010fa0]non-existing PPS referenced
[h264 @ 0xa010fa0]B picture before any references, skipping
[h264 @ 0xa010fa0]decode_slice_header error
[h264 @ 0xa010fa0]no frame!
[h264 @ 0xa010fa0]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0xa010fa0]decode_slice_header error
[h264 @ 0xa010fa0]no frame!
[h264 @ 0xa010fa0]non-existing PPS referenced
[h264 @ 0xa010fa0]B picture before any references, skipping
[h264 @ 0xa010fa0]decode_slice_header error
[h264 @ 0xa010fa0]no frame!

Seems stream 0 codec frame rate differs from container frame rate: 59.94 (60000/1001) -> 29.97 (30000/1001)

Seems stream 2 codec frame rate differs from container frame rate: inf (1/0) -> -nan (0/0)
Input #0, mpegts, from 'test.flv':
  Duration: N/A, start: 1833.702989, bitrate: N/A
  Program 1 
    Stream #0.0[0x44]: Video: h264, yuv420p, 720x480 [PAR 128:81 DAR 64:27], 29.97 tbr, 90k tbn, 59.94 tbc
Output #0, mp3, to 'test.mp3':
    Stream #0.0: Audio: libmp3lame, 0 channels, s16, 128 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
[mp3 @ 0xa0a9eb0]sample rate not set
Could not write header for output file #0 (incorrect codec parameters ?)


```

I also tried this line (someone advised it somewhere):
```
ffmpeg -i "test.flv" -acodec libmp3lame -ab 128k -ar 44100 "test.mp3"
```And the error:
```

    Last message repeated 1 times
[h264 @ 0x8a2efa0]decode_slice_header error
[h264 @ 0x8a2efa0]no frame!
[h264 @ 0x8a2efa0]non-existing PPS referenced
[h264 @ 0x8a2efa0]B picture before any references, skipping
[h264 @ 0x8a2efa0]decode_slice_header error
[h264 @ 0x8a2efa0]no frame!
[h264 @ 0x8a2efa0]non-existing PPS referenced
[h264 @ 0x8a2efa0]B picture before any references, skipping
[h264 @ 0x8a2efa0]decode_slice_header error
[h264 @ 0x8a2efa0]no frame!
[h264 @ 0x8a2efa0]non-existing PPS referenced
[h264 @ 0x8a2efa0]B picture before any references, skipping
[h264 @ 0x8a2efa0]decode_slice_header error
[h264 @ 0x8a2efa0]no frame!
[h264 @ 0x8a2efa0]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0x8a2efa0]decode_slice_header error
[h264 @ 0x8a2efa0]no frame!
[h264 @ 0x8a2efa0]non-existing PPS referenced
[h264 @ 0x8a2efa0]B picture before any references, skipping
[h264 @ 0x8a2efa0]decode_slice_header error
[h264 @ 0x8a2efa0]no frame!

Seems stream 0 codec frame rate differs from container frame rate: 59.94 (60000/1001) -> 29.97 (30000/1001)

Seems stream 2 codec frame rate differs from container frame rate: inf (1/0) -> -nan (0/0)
Input #0, mpegts, from 'test.flv':
  Duration: N/A, start: 1833.702989, bitrate: N/A
  Program 1 
    Stream #0.0[0x44]: Video: h264, yuv420p, 720x480 [PAR 128:81 DAR 64:27], 29.97 tbr, 90k tbn, 59.94 tbc
Output #0, mp3, to 'test.mp3':
    Stream #0.0: Audio: libmp3lame, 44100 Hz, 0 channels, s16, 128 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
Press [q] to stop encoding
[NULL @ 0x8b24610]non-existing PPS referenced
    Last message repeated 54 times
[NULL @ 0x8a2efa0]non-existing PPS referenced
    Last message repeated 224 times
[NULL @ 0x8b24610]non-existing PPS referenced
    Last message repeated 247 times bitrate=   0.0kbits/s    
[NULL @ 0x8a2efa0]missing picture in access unit
    Last message repeated 1 times
[NULL @ 0x8b24610]missing picture in access unit
size=       1kB time=0.05 bitrate= 132.8kbits/s    
video:0kB audio:1kB global headers:0kB muxing overhead 3.832335%

```Does anyone know how to solve this?

regards

---

### Post by andrew.46 on 2011-11-21
Can you post the problem file somewhere?

---

### Post by Chiel92 on 2011-11-21
Well, i'd like to, but it's size is about 500 MB...
It's a complete concert, which I want to convert to mp3.

I can't cut it using ffmpeg, cause that gives similar errors.

---

### Post by FakeOutdoorsman on 2011-11-21
0 channels doesn't look quite right. Did you try this?
```
ffmpeg -i test.flv -acodec libmp3lame -ab 128k -ar 44100 -ac 2 test.mp3
```
Do you have libmp3lame enabled? See *Option B* here if you're not sure:
[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

If my command fails then try a more recent FFmpeg:
[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

You can shorten the FFmpeg compile guide if you just want to test a new ffmpeg:
[list]
[*]Skip x264 and libvpx
[*]Dependencies: build-essential libmp3lame-dev git
[*]FFmpeg configure: --enable-gpl --enable-libmp3lame
[*]Skip checkinstall and just run ./ffmpeg binary in ~/ffmpeg
[/list]

---

### Post by Chiel92 on 2011-11-21
Thanks for your reply.

The following:
```
 ffmpeg -i test.flv -acodec libmp3lame -ab 128k -ar 44100 -ac 2 test.mp3
```      [FONT=monospace]
gives same errors, except that "0 channels" changes in "stereo".

Both of the HOWTO's do not work.
I think they're out-of-date. At least many of the packages cannot be found.

Re-installing ffmpeg didnt help.


It might be useful to mention that I created the flv by ripping a cd.
[/FONT]

---

### Post by FakeOutdoorsman on 2011-11-21
> **Chiel92 said:**
> The following:
```
 ffmpeg -i test.flv -acodec libmp3lame -ab 128k -ar 44100 -ac 2 test.mp3
```      [FONT=monospace]
gives same errors, except that "0 channels" changes in "stereo".
Same errors, as in...?
```
[mp3 @ 0xa0a9eb0]sample rate not set
Could not write header for output file #0 (incorrect codec parameters ?)
```

> **Chiel92 said:**
> Both of the HOWTO's do not work.
What do you mean by "do not work"?

> **Chiel92 said:**
> I think they're out-of-date.
They shouldn't be out of date. I updated the compile guide a few days ago. What version of Ubuntu are you using?

> **Chiel92 said:**
> At least many of the packages cannot be found.
What packages can not be found? Can you show the output of your apt install command?

> **Chiel92 said:**
> Re-installing ffmpeg didnt help.
Can you elaborate?

> **Chiel92 said:**
> It might be useful to mention that I created the flv by ripping a cd.
What was the command/program/procedure you used to do this?

---

### Post by Chiel92 on 2011-11-21
> Same errors, as in...?```

ffmpeg -i test.flv -acodec libmp3lame -ab 128k -ar 44100 -ac 2 test.mp3

```says:
```

...
...
[h264 @ 0x8167fa0]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0x8167fa0]decode_slice_header error
[h264 @ 0x8167fa0]no frame!
[h264 @ 0x8167fa0]non-existing PPS referenced
[h264 @ 0x8167fa0]B picture before any references, skipping
[h264 @ 0x8167fa0]decode_slice_header error
[h264 @ 0x8167fa0]no frame!

Seems stream 0 codec frame rate differs from container frame rate: 59.94 (60000/1001) -> 29.97 (30000/1001)

Seems stream 2 codec frame rate differs from container frame rate: inf (1/0) -> -nan (0/0)
Input #0, mpegts, from 'test.flv':
  Duration: N/A, start: 1833.702989, bitrate: N/A
  Program 1 
    Stream #0.0[0x44]: Video: h264, yuv420p, 720x480 [PAR 128:81 DAR 64:27], 29.97 tbr, 90k tbn, 59.94 tbc
Output #0, mp3, to 'test.mp3':
    Stream #0.0: Audio: libmp3lame, 44100 Hz, stereo, s16, 128 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
Press [q] to stop encoding
[NULL @ 0x825d610]non-existing PPS referenced
    Last message repeated 54 times
[NULL @ 0x8167fa0]non-existing PPS referenced
    Last message repeated 224 times
[NULL @ 0x825d610]non-existing PPS referenced
    Last message repeated 247 times bitrate=   0.0kbits/s    
[NULL @ 0x8167fa0]missing picture in access unit
    Last message repeated 1 times
[NULL @ 0x825d610]missing picture in access unit
size=       1kB time=0.05 bitrate= 132.8kbits/s    
video:0kB audio:1kB global headers:0kB muxing overhead 3.832335%

```> What do you mean by "do not work"? They shouldn't be out of date. I updated the compile guide a few days ago. What version of Ubuntu are you using? What packages can not be found? Can you show the output of your apt install command?Ah, excuse me. I indeed didn't read carefully about the ubuntu versions. Sorry, my mistake. The first howto about the mp3 lame lib works fine, and says that I already have them installed. The second one will not work, I guess, as I run ubuntu 10.04. (See profile on the right)

> What was the command/program/procedure you used to do this?I used the GUI from VLC to do this. Before that succeeded, I needed to install some extra things, namely:
```
sudo apt-get install libdvdread4
```and```

sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by andrew.46 on 2011-11-21
> **Chiel92 said:**
> Well, i'd like to, but it's size is about 500 MB...

That's what broadband is for :).

---

