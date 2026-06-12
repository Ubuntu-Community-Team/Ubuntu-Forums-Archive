---
title: "a Good screen recorder?"
date: 2011-07-29
forum: Multimedia Software
---

### Post by Partian on 2011-07-29
I need a recorder that I can record a window or a custom size.
is there any?

---

### Post by hakermania on 2011-07-29
I use recordmydesktop gtk and can record in 720p Max plus sound from microphone ;) its on the repos ;)

---

### Post by Partian on 2011-07-29
> **hakermania said:**
> I use recordmydesktop gtk and can record in 720p Max plus sound from microphone ;) its on the repos ;)

What's the repos?
and could I have a link toit, as it's not in the SOftware Centre

---

### Post by hakermania on 2011-07-29
its in the repos = its in the repositories ;)
Are you sure about that?
[http://img707.imageshack.us/img707/9813/screenshotubuntusoftwari.png](http://img707.imageshack.us/img707/9813/screenshotubuntusoftwari.png)

---

### Post by NightwishFan on 2011-07-29
If you do not see it you might need to go to edit->software sources and enable "Universe".

I use ffmpeg with x11grab from the command line myself. If you aren't afraid of the command line it works great.

---

### Post by Partian on 2011-07-29
> **hakermania said:**
> its in the repos = its in the repositories ;)
Are you sure about that?
[http://img707.imageshack.us/img707/9813/screenshotubuntusoftwari.png](http://img707.imageshack.us/img707/9813/screenshotubuntusoftwari.png)

You said: recordmydesktop
Not: Desktop Recorder..

---

### Post by Partian on 2011-07-29
> **NightwishFan said:**
> If you do not see it you might need to go to edit->software sources and enable "Universe".

I use ffmpeg with x11grab from the command line myself. If you aren't afraid of the command line it works great.

Sorted it, and is there any tutorials of that on YouTube do you think?
I had a brief search just before and no look

---

### Post by hakermania on 2011-07-29
> **Partian said:**
> You said: recordmydesktop
Not: Desktop Recorder..
See what I've placed in the search field on the screenshot :)

---

### Post by NightwishFan on 2011-07-29
Well if you ever want to try ffmpeg (only really if recordmydesktop-gtk doesn't suit you) I have a few scripts that give great results. The only parameter you need to change is the **size** (-s wxga). You might have to do research to add audio recording to it (i always dub the audio in afterward).

Press CTRL+C to stop the recording.

For systems with only free codecs try:
```
ffmpeg -f x11grab -s wxga -r 24 -b 6500 -bt 256k -an -threads 2 -sameq -i :0.0 out.avi
```

For systems that include x264 use this for better quality/performance:
```
ffmpeg -f x11grab -r 25 -s 1366x768 -i :0.0 -vcodec libx264 -vpre lossless_ultrafast -crf 22 -an -threads 2 screencast.mkv
```

---

### Post by FakeOutdoorsman on 2011-07-31
> **NightwishFan said:**
> Well if you ever want to try ffmpeg (only really if recordmydesktop-gtk doesn't suit you) I have a few scripts that give great results. The only parameter you need to change is the **size** (-s wxga). You might have to do research to add audio recording to it (i always dub the audio in afterward).

Press CTRL+C to stop the recording.

For systems with only free codecs try:
```
ffmpeg -f x11grab -s wxga -r 24 -b 6500 -bt 256k -an -threads 2 -sameq -i :0.0 out.avi
```
*-sameq* and *-b* are mutually exclusive, meaning if you use one you can't use the other (or ffmpeg will ignore one). *-sameq* means "use same quantizer as source". The documentation for this option was fairly misleading in the past, but it has been slighly updated upstream.

For a good tutorial see [HOWTO: Proper Screencasting on Linux](http://ubuntuforums.org/showthread.php?t=1392026).

---

### Post by NightwishFan on 2011-07-31
Yeah, I know, obviously. I just missed that. Regardless it still works.

---

