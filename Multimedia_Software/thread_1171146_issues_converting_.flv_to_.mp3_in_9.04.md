---
title: "issues converting .flv to .mp3 in 9.04"
date: 2009-05-27
forum: Multimedia Software
---

### Post by franklovecchio on 2009-05-27
Hi,

I have tried winff, a few scripts, and plain 'ol ffmpeg one file at a time; but for the life of me, I can't seem to convert an flv file to an mp3 file.

I get acodec and libmp3lame errors, but before I go into detail, are there any up to date scripts out there for batch converting?  I feel as if all the forum posts are older and have not worked for me.

---

### Post by andrew.46 on 2009-05-27
Hi franklovecchio,

> **franklovecchio said:**
> I have tried winff, a few scripts, and plain 'ol ffmpeg one file at a time; but for the life of me, I can't seem to convert an flv file to an mp3 file.

It should not be too difficult as the standard low quality flv usually has mp3 sound in the first place. Cam I give a demonstration? Below are the details of a standard flv, these results are from 'ffmpeg -i panda.flv':

```

Input #0, flv, from 'panda.flv':
Duration: 00:00:16.06, start: 0.000000, bitrate: 64 kb/s
Stream #0.0: Video: flv, yuv420p, 320x240, 57.92 tbr, 1k tbn, 1k tbc
**[COLOR="Purple"]Stream #0.1: Audio: mp3, 22050 Hz, mono, s16, 64 kb/s[/COLOR]**

```

So to copy the sound to mp3 the following is required:

```

andrew@skamandros~/samples$ **[COLOR="Purple"]ffmpeg -i panda.flv -acodec copy test.mp3[/COLOR]**
FFmpeg version SVN-r18929, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --prefix=/usr --mandir=/usr/man --disable-debug
 --enable-shared --disable-static --enable-postproc --enable-avfilter
--enable-pthreads --enable-libtheora --enable-libvorbis --enable-x11grab
 --enable-libmp3lame --enable-libx264 --enable-libschroedinger 
--enable-libfaac --enable-libfaad --enable-libamr-wb --enable-libamr-nb
 --enable-libgsm --enable-libspeex --enable-zlib --enable-nonfree --enable-gpl
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.29. 0 / 52.29. 0
  libavformat   52.33. 0 / 52.33. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    0. 5. 0 /  0. 5. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on May 24 2009 21:28:23, gcc: 4.2.4
[flv @ 0x8069440]skipping flv packet: type 18, size 294, flags 0

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 57.92 (695/12)
Input #0, flv, from 'panda.flv':
  Duration: 00:00:16.06, start: 0.000000, bitrate: 64 kb/s
    Stream #0.0: Video: flv, yuv420p, 320x240, 57.92 tbr, 1k tbn, 1k tbc
    Stream #0.1: Audio: mp3, 22050 Hz, mono, s16, 64 kb/s
[B][COLOR="Purple"]Output #0, mp3, to 'test.mp3':
    Stream #0.0: Audio: libmp3lame, 22050 Hz, mono, s16, 64 kb/s[/COLOR][/B]
Stream mapping:
  Stream #0.1 -> #0.0
Press [q] to stop encoding
size=     126kB time=16.09 bitrate=  64.0kbits/s    
video:0kB audio:126kB global headers:0kB muxing overhead 0.024858%

```

It all depends on the makeup of the flv which can vary a little but it does not get too much harder than that.

Andrew

---

### Post by franklovecchio on 2009-05-28
Ok, I can convert the flv file no problem, but it seems I've pin-pointed the problem.  I tried to convert the mp3 file to stereo, and got the same error as when I was using a script to batch convert the flv files, which is "(eca-engine) WARNING: An output object has raised an error! Possible causes: Out of disk space, permission denied, unable to launch external applications needed in processing, etc."


```

sudo ecasound -i flv_converted_file.mp3 -etf:8 -o stereo_file.mp3
********************************************************************************
*        ecasound v2.5.2 (C) 1997-2008 Kai Vehmanen and others    
********************************************************************************
- [ Session created ] ----------------------------------------------------------
- [ Chainsetup created (cmdline) ] ---------------------------------------------
- [ Connecting chainsetup ] ----------------------------------------------------
(eca-chainsetup) 'nonrt' buffering mode selected.
(eca-chainsetup) NOTE: using existing audio parameters -f:s16_le,2,22050 for 
... object 'flv_converted_file.mp3 (tried to open with -f:s16_le,2,44100).
(eca-chainsetup) Opening input "flv_converted_file.mp3", mode "read". Format: s16_le, 
... channels 2, srate 22050, interleaved (locked params).
(eca-chainsetup) Opening output "stereo_file.mp3", mode "write". Format: 
... s16_le, channels 2, srate 22050, interleaved (locked params).
- [ Chainsetup connected ] -----------------------------------------------------
(eca-control-objects) Connected chainsetup: "command-line-setup".
- [ Controller/Starting batch processing ] -------------------------------------
- [ Engine init - Driver start ] -----------------------------------------------
(audioio-mp3) Starting to encode stereo_file.mp3 with lame.
(audioio-mp3) Attempt to write after child process has terminated.
(eca-engine) WARNING: An output object has raised an error! Possible causes: Out 
... of disk space, permission denied, unable to launch external applications needed in 
... processing, etc.
- [ Controller/Batch processing finished (-3) ] --------------------------------
ecasound: Warning! Errors detected during processing.
(eca-control-objects) Disconnecting chainsetup: "command-line-setup".
- [ Chainsetup disconnected ] --------------------------------------------------


```

---

### Post by paul.gevers on 2009-05-28
> **franklovecchio said:**
> I get acodec and libmp3lame errors, but before I go into detail, are there any up to date scripts out there for batch converting?  I feel as if all the forum posts are older and have not worked for me.

I agree with andrew.46 but, the problem mentioned above is probably related to the fact that you did not install libavcodec-unstripped-51 or 52 (depending on whether you are on intrepid or jaunty). Best way to install it for the future is by installing ubuntu-restricted-extras or kubuntu-restricted-extras or xubuntu-restricted-extras 

Greetings,

---

### Post by Zach-Warlock on 2009-06-18
> **andrew.46 said:**
> Hi franklovecchio,



It should not be too difficult as the standard low quality flv usually has mp3 sound in the first place. Cam I give a demonstration? Below are the details of a standard flv, these results are from 'ffmpeg -i panda.flv':

```

Input #0, flv, from 'panda.flv':
Duration: 00:00:16.06, start: 0.000000, bitrate: 64 kb/s
Stream #0.0: Video: flv, yuv420p, 320x240, 57.92 tbr, 1k tbn, 1k tbc
**[COLOR=Purple]Stream #0.1: Audio: mp3, 22050 Hz, mono, s16, 64 kb/s[/COLOR]**

```So to copy the sound to mp3 the following is required:

```

andrew@skamandros~/samples$ **[COLOR=Purple]ffmpeg -i panda.flv -acodec copy test.mp3[/COLOR]**
FFmpeg version SVN-r18929, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --prefix=/usr --mandir=/usr/man --disable-debug
 --enable-shared --disable-static --enable-postproc --enable-avfilter
--enable-pthreads --enable-libtheora --enable-libvorbis --enable-x11grab
 --enable-libmp3lame --enable-libx264 --enable-libschroedinger 
--enable-libfaac --enable-libfaad --enable-libamr-wb --enable-libamr-nb
 --enable-libgsm --enable-libspeex --enable-zlib --enable-nonfree --enable-gpl
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.29. 0 / 52.29. 0
  libavformat   52.33. 0 / 52.33. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    0. 5. 0 /  0. 5. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on May 24 2009 21:28:23, gcc: 4.2.4
[flv @ 0x8069440]skipping flv packet: type 18, size 294, flags 0

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 57.92 (695/12)
Input #0, flv, from 'panda.flv':
  Duration: 00:00:16.06, start: 0.000000, bitrate: 64 kb/s
    Stream #0.0: Video: flv, yuv420p, 320x240, 57.92 tbr, 1k tbn, 1k tbc
    Stream #0.1: Audio: mp3, 22050 Hz, mono, s16, 64 kb/s
[B][COLOR=Purple]Output #0, mp3, to 'test.mp3':
    Stream #0.0: Audio: libmp3lame, 22050 Hz, mono, s16, 64 kb/s[/COLOR][/B]
Stream mapping:
  Stream #0.1 -> #0.0
Press [q] to stop encoding
size=     126kB time=16.09 bitrate=  64.0kbits/s    
video:0kB audio:126kB global headers:0kB muxing overhead 0.024858%

```It all depends on the makeup of the flv which can vary a little but it does not get too much harder than that.

Andrew

Thanks that worked for me:p

---

