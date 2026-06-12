---
title: "Convert FLV to MP3 COMPLETELY!"
date: 2009-09-18
forum: Multimedia Software
---

### Post by itzmcgin on 2009-09-18
Ok here is the problem, a youtube video contains a aac audio. The File itself is flv, but when i rip the audio i get aac. How can i just convert the flv file to mp3 and make sure the audio type is changed to mp3 and not aac? Any Ideas? Thanks!

---

### Post by itzmcgin on 2009-09-18
I am using FFMPEG, forgot to mention that.

---

### Post by FakeOutdoorsman on 2009-09-18
1. Enable restricted encoders in FFmpeg:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

2. Encode to MP3.  I'm assuming you're using Ubuntu Jaunty:
```
ffmpeg -i input.flv -ab 192k output.mp3
```

You can adjust the bitrate with the **-ab** option.

---

### Post by itzmcgin on 2009-09-19
That didnt work, it converts it to mp3 but it says 0kb. The size completely gets reduced for some reason.

---

### Post by SuperSonic4 on 2009-09-19
```
ffmpeg -i input.flv -vn -acodec libmp3lame -ac 2 -ab 128k output.mp3
```

[list]
[*]**-vn** means **no video codec** (ie: audio only)
[*]**-acodec libmp3lame** means use lame for audio 
[*]**-ac 2** means rip into stereo
[*]**-ab 128k** means rip into 128kbps
[/list]

---

### Post by itzmcgin on 2009-09-19
My bad didnt see step 1, i read it but not sure how to work with that guide. what is terminal, i dont have that? Please explain a bit more if you could, thanks.

---

### Post by SuperSonic4 on 2009-09-19
Press Alt+F2 and type gnome-terminal in the box and hit return

---

### Post by itzmcgin on 2009-09-19
ok i got that to work, also now it converts it to mp3 and gives me the size, but the size is exactly the same size as the video. shouldnt it be like 2-3mb? It doesnt play anyway so yea. Yea i do want audio only, and it opened as audio only but not working still. Any other ideas?

---

### Post by ken_do_san on 2009-09-19
Try Mobile Media Converter, converts .flv to most common media formats (including mp3).

---

