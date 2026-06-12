---
title: "[SOLVED] My computer can't handle h.264 codec video, is there a way to convert it?"
date: 2008-08-21
forum: Multimedia Software
---

### Post by Julita on 2008-08-21
Hello everyone! I have encountered a problem that nearly killed me! I have a video in .mkv format, 720p, with video codec h.264. I have tried different kinds of players, but none of them can cope with it. Since my computer is rather old (Pentuim III, 1GHz) and my video card as well, I presume that the best option for me would be to convert everything and set smaller video resolution. Is there a way to do that? Please, guys, help, it's urgent...

---

### Post by shirilover on 2008-08-21
There is a way. You can use avidemux to re-encode and/or resize the video.
Load your video using the open button.
In the drop-down list for video, select MPEG-4 ASP(Xvid4).

Click the filters button.
In the transform section, select MPlayer resize and click the large '+' button to add the filter.
Enter the width and height for the new file (704x396 is probably a safe choice).
If the file had subtitles, you would need to extract them using mkvextract(part of mkvtoolnix), then add them using the subtitles section.

Configure the xvid encoding options by clicking the configure button.
In the main tab: 
I recommend checkin turbo mode and chroma optimizer.
If you good quality, choose two pass-video size(enter desired video size in text box) or two pass average bitrate from the drop-down list. If you'd rather have faster encoding, then choose single pass - bitrate(1200 is a good choice for most).
In the motion & misc tab:
Select 4 - Wide search for VHQ mode
Use 3 b-frames.
I-frame interval can be changed depending on the framrate of the original video file(for 29.97 fps, use max 300; for 23.976, use 240).
In the quantization tab:
Check the box for trellis quantization.
Click OK when finished.

Configure audio format by choosing MP3 (LAME) from the drop-down list.
You can change the bitrate by clicking the configure button and selecting the bitrate you want from the drop-down list.
When finished, click the save button and give your new file a name.

Depending on the length of the video and your encodingg options, it can take a few hours to finish.

---

### Post by Julita on 2008-08-24
Dear shirilover, thank you very much!!! Everything worked perfectly for me!!!

---

