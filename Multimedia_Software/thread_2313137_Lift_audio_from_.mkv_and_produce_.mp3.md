---
title: "Lift audio from .mkv and produce .mp3"
date: 2016-02-09
forum: Multimedia Software
---

### Post by Owen Thomas on 2016-02-09
Hello.

I recently used HandBrake to rip a track from a DVD. The only format supported by this software is .mkv, and while I can watch the video, others that have used their own devices to view the same video cannot.

The video component is redundant: I am only interested in the audio component as there is no image other than one that says "Audio Only Recording". Hence, I would like to transcode this recording from .mkv to .mp3 because I believe this would reduce the file's size considerably, as well as dispensing with the redundant video and making the recording available over a commonly recognised media type.

Your suggestions on what software I can use to do this are appreciated.

  Owen.

---

### Post by shantiq on 2016-02-10
hi owen


this will do that: [in your terminal]


```
 avconv -i nameofyourfile.mkv   -vn  -b:a 192k nameofyourfile.mp3
```


-vn  means no video    192k can be 128 or 256    up to you

---

### Post by Owen Thomas on 2016-02-10
Thanks shantiq, that appears to have given me what I want.

---

### Post by mörgæs on 2016-02-10
Good, then please mark the thread 'solved'.

---

### Post by Yellow Pasque on 2016-02-10
[https://trac.handbrake.fr/wiki/SupportFAQ#just-audio](https://trac.handbrake.fr/wiki/SupportFAQ#just-audio)

---

### Post by SeijiSensei on 2016-02-10
You can also extract the audio track from a Matroska container with mkvextract, one of the programs in the mkvtoolnix package.

---

### Post by FakeOutdoorsman on 2016-02-10
Using ffmpeg:

```
ffmpeg -i input.mkv -c:a libmp3lame -q:a 4 output.mp3
```

As a bash for loop to do a batch:

```
for f in *.mkv; do ffmpeg -i "$f" -c:a libmp3lame -q:a 4 "${f%.mkv}.mp3"; done
```

See [FFmpeg Wiki: MP3 Encoding Guide](http://trac.ffmpeg.org/wiki/Encode/MP3).

---

