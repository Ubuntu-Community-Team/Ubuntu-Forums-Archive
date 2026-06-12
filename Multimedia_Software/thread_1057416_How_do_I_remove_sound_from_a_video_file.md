---
title: "How do I remove sound from a video file?"
date: 2009-02-01
forum: Multimedia Software
---

### Post by Rytron on 2009-02-01
Hi.
How do I remove sound from a video file? I dont want the audio, I just want the video file with no sound.
Thanks.

---

### Post by Prospero2006 on 2009-02-01
Download Cinelerra. 
When you import the video file into the editor, the audio tracks will be
separated out. You will be able to delete the audio tracks and render the video out to an .mpg file.

Open Movie Editor should also work.

---

### Post by Rytron on 2009-02-01
It worked perfectly. Thank you Prospero2006.

---

### Post by andrew.46 on 2009-02-03
Hi,

It can also be done with FFmpeg by using the -vn option:

> -vn Disable video recording.

Andrew

---

### Post by gackt on 2009-02-03
Marked as solved plz!

---

### Post by Rytron on 2009-02-03
> **gackt said:**
> Marked as solved plz!

The function to mark the thread as solved is gone.

---

### Post by Rytron on 2009-02-03
> **andrew.46 said:**
> Hi,

It can also be done with FFmpeg by using the -vn option:



Andrew

Hi Andrew. How would the code go?

---

### Post by FakeOutdoorsman on 2009-02-03
> **Rytron said:**
> Hi Andrew. How would the code go?
First determine the audio format:
```
ffmpeg -i input.flv
```
FFmpeg will give a full output, but here's the important part:
```
Stream #0.1: Audio: mp3, 44100 Hz, stereo, s16, 80 kb/s
```
Now that I know it is mp3, I can give the correct output file extension:
```
ffmpeg -i input.flv -acodec copy output.mp3
```
Using "acodec copy" will just copy the audio stream and not re-encode it.  This preserves the quality.  Sometimes you will need to use "-vn" as Andrew mentioned because some containers, mp4 and ogg for example, can take both audio and video.

---

### Post by FakeOutdoorsman on 2009-02-03
Vidiot.  I just now read that you want the video instead of the audio:
```
ffmpeg -i input.flv -an -vcodec copy output.flv
```
The "an" option tells FFmpeg to ignore the audio.  Like my previous example, this just copies the video stream and doesn't re-encode.

---

### Post by andrew.46 on 2009-02-03
> **FakeOutdoorsman said:**
> Vidiot. 


Oops! Vidiot +1 :-)

Andrew

---

### Post by Rytron on 2009-02-03
Thank you andrew.46 & FakeOutdoorsman. Easy mistake to make. The wording of the question can be misleading.

---

### Post by Rytron on 2009-02-03
> **FakeOutdoorsman said:**
> Vidiot.  I just now read that you want the video instead of the audio:
```
ffmpeg -i input.flv -an -vcodec copy output.flv
```
The "an" option tells FFmpeg to ignore the audio.  Like my previous example, this just copies the video stream and doesn't re-encode.

This is excellent. I presume the same code can be used for any video format?
i.e.
ffmpeg -i input.**avi** -an -vcodec copy output.**avi**

---

### Post by FakeOutdoorsman on 2009-02-03
> **Rytron said:**
> This is excellent. I presume the same code can be used for any video format?
i.e.
ffmpeg -i input.**avi** -an -vcodec copy output.**avi**
It should work with most video formats.  I think.

---

### Post by Rytron on 2009-02-03
> **FakeOutdoorsman said:**
> It should work with most video formats.  I think.

Thanks again buddy.

---

### Post by Rytron on 2009-06-20
> **FakeOutdoorsman said:**
> Vidiot.  I just now read that you want the video instead of the audio:
```
ffmpeg -i input.flv -an -vcodec copy output.flv
```
The "an" option tells FFmpeg to ignore the audio.  Like my previous example, this just copies the video stream and doesn't re-encode.

Hi.
Is there an equivalent command for ogv files?

Edit: It's okay, I used VFFF.

---

