---
title: "How can I convert raw YUV video data to a useable format like AVI?"
date: 2007-12-20
forum: Multimedia &amp; Video
---

### Post by YAOMTC on 2007-12-20
Since I couldn't get that enormously huge MythTV to work at all, I was suggested to check out xawtv. It certainly doesn't look nice at all (much unlike TVtime), and is a pain to set up, but it does what I need it to do: it records. Unfortunately, the only thing I can get from that is raw YUV video data. Is there any way to make this into a format like AVI or MPEG, or any other format I can actually work with?

**EDIT:** While experimenting with what was suggested in the mjpegtools manual, I tried this:
```
lavrec -f q -i n -d 1 -q 80 -s -l 80 -R l -U record.avi
```
At first when I tried this, I had tvtime up to see if I could watch what I was recording while it recorded... When I entered that command, tvtime went to static and this error happened:
```
++ WARN: [lavrec] Unable to set negative priority for audio thread.
++ WARN: [lavrec] Pthread Real-time scheduling for audio thread could not be enabled.
**ERROR: [lavrec] Error getting video parameters: Invalid argument
Segmentation fault (core dumped)
chris@YAOMTC-1:~$ lavrec -f q -i n -d 1 -q 80 -s -l 80 -R l -U record.avi
++ WARN: [lavrec] Unable to set negative priority for audio thread.
++ WARN: [lavrec] Pthread Real-time scheduling for audio thread could not be enabled.
**ERROR: [lavrec] Error getting video parameters: Invalid argument
Segmentation fault (core dumped)
```
I tried it again without tvtime up, and I got the same thing.

---

### Post by yabbies on 2007-12-20
need mjpegtools

```
cat stream.yuv | yuvfps -r 30000:1001 | yuvscaler -n n -O DVD |
mpeg2enc -n n -f 8 -F 4 -o out.m2v
```

if your original file has correct fps 29.970 for NTSC
and the ratio is 720x480 for NTSC you can use

```
cat stream.yuv | mpeg2enc -n n -f 8 -F 4 -o out.m2v

```

---

### Post by YAOMTC on 2007-12-20
Does it have to be planar YUV rather than (packed, YUYV)? It seems I can't record in planar YUV, as I get an error when I try to do so.

Also, I can't get the width of the window to be 720. It just jumps between 736 and 704. Quite annoying.

---

### Post by YAOMTC on 2007-12-20
.

---

### Post by YAOMTC on 2007-12-20
.

---

### Post by YAOMTC on 2007-12-20
.

---

### Post by YAOMTC on 2007-12-21
.

---

### Post by disturbedite on 2007-12-21
avidemux can convert raw video.  i was using it just for that two days ago & yesterday...

---

### Post by YAOMTC on 2007-12-21
Okay, I've gotten rid of xawtv and got motv, which is basically the same thing but with a much better GUI. When I try to record *planar* YUV, this is what I get:
> no way to get: 320x240 16 bit YUV 4:2:2 (planar)
So I record it in the (packed, YUYV) format, and... well, avidemux can't work with that, and I  bet ffmpeg or mjpegtools can't, either... What *can* work with this?!

Man, this is frustrating.

---

### Post by yabbies on 2007-12-21
dude, mjpegtools was specifically designed to edit, playback and compress for xawtv
I gave you a code for ntsc yuv
I live in usa so I don't know what the code for PAL would be, you can easily do some reading in the man pages for mjpegtools 

good luck and Merry Christmas

[mjpegtools]("http://mjpeg.sourceforge.net/")

---

### Post by YAOMTC on 2007-12-21
Well, yeah, it's NTSC, but the first code didn't work, and I can't get the size to be 720x480. (Isn't that widescreen? I'm recording SNES gameplay, which is fullscreen)

I take it the man pages for mjpegtools isn't in /usr/share/doc/mjpegtools, because all that's in there is AUTHORS, changelog, and copyright... Where *are* man pages usually, anyway? I'll look at the stuff on their SourceForge page for now.

---

### Post by YAOMTC on 2007-12-21
Okay, while experimenting with what was suggested in the mjpegtools manual, I tried this:
```
lavrec -f q -i n -d 1 -q 80 -s -l 80 -R l -U record.avi
```
At first when I tried this, I had tvtime up to see if I could watch what I was recording while it recorded... When I entered that command, tvtime went to static and this error happened:
```
++ WARN: [lavrec] Unable to set negative priority for audio thread.
++ WARN: [lavrec] Pthread Real-time scheduling for audio thread could not be enabled.
**ERROR: [lavrec] Error getting video parameters: Invalid argument
Segmentation fault (core dumped)
chris@YAOMTC-1:~$ lavrec -f q -i n -d 1 -q 80 -s -l 80 -R l -U record.avi
++ WARN: [lavrec] Unable to set negative priority for audio thread.
++ WARN: [lavrec] Pthread Real-time scheduling for audio thread could not be enabled.
**ERROR: [lavrec] Error getting video parameters: Invalid argument
Segmentation fault (core dumped)
```
I tried it again without tvtime up, and I got the same thing.

I think I'll bring up the VCR and do a new setup, using a VHS to record for now, and I'll record the playback of the VHS when this is worked out (if it is).

---

### Post by YAOMTC on 2007-12-22
Alright, I've got my Super Nintendo (I'm recording some Earthbound gameplay) hooked up to my VCR, which is hooked up to my tuner card. This doesn't change anything, besides that things are easier now.

---

### Post by YAOMTC on 2007-12-22
.

---

### Post by YAOMTC on 2007-12-22
.

---

### Post by YAOMTC on 2007-12-23
.

---

### Post by YAOMTC on 2007-12-24
.

---

### Post by YAOMTC on 2007-12-26
.

---

### Post by YAOMTC on 2007-12-26
.

---

### Post by YAOMTC on 2007-12-27
.

---

### Post by YAOMTC on 2007-12-27
.

---

### Post by YAOMTC on 2007-12-27
.

---

### Post by YAOMTC on 2007-12-30
.

---

### Post by YAOMTC on 2008-01-01
Maybe I should just give up on this one, it seems nobody knows the answer. :(

---

