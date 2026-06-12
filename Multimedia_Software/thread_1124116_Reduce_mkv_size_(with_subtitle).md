---
title: "Reduce mkv size (with subtitle)"
date: 2009-04-13
forum: Multimedia Software
---

### Post by Browser_ice on 2009-04-13
How can I reduce the size of an MKV file that contains subtitles and still keep the subtitles intact and synchronized ? 

My video card has lots of performance issues when video is greather then 1024x768.

I don't mind a reduction in quality as long as it is acceptable.

---

### Post by lovinglinux on 2009-04-13
I have method in which you will resize the video without the subtitles using WinFF, then replace the original video/audio streams inside the mkv container using mkvtoolnix.

Steps:

1 - Backup the mkv file just in case something goes wrong

2 - Install mkvtoolnix and WinFF

*download the deb file from [http://code.google.com/p/winff/](http://code.google.com/p/winff/)*

```
sudo apt-get install mkvtoolnix
```

3 - Open WinFF from "Applications >>> Sound & Video >>> WinFF"

4 - Add the mkv video you want to convert, select the options "AVI" and "Xvid in AVI (16:9)", select the output folder and specify the "Video Size" you want in the "Additional Options", then click "Convert" and wait for the conversion to finish.

5 - Open "Applications >>> Sound & Video >>> MKV File Creator"

6 - In the "Input" tab, hit the "add" button and select the original mkv file.

7 - Untick the video and the audio streams in the "Tracks" input field, leaving only the subtitle track activated.

8 - Hit the "add" button again and select the converted/resized AVI file.

9 - Click the "Browse" button next to the "Output filename" input field and select another folder to save the new mkv video and click "Save".

10 - Click "Start Muxing"

---

