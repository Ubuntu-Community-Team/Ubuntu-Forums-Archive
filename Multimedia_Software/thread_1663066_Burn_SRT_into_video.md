---
title: "Burn SRT into video?"
date: 2011-01-09
forum: Multimedia Software
---

### Post by marshall1001 on 2011-01-09
I recently downloaded some non-english language films as well as the associated .srt files containing the subtitles. I was just wondering whether or not it was possible to burn/encode the subtitles from the file onto the video itself?

I know its possible to encode subtitles onto video because I've done it when ripping DVDs but I've never done it via SRT. Any ideas?

---

### Post by paparozoumis on 2011-01-09
Avidemux is the tool you need

---

### Post by marshall1001 on 2011-01-09
Thank you. Is there any special trick to using it it or is it self-explanatory?

---

### Post by Symbioosi on 2011-01-31
I had this same problem with .flv video file and .srt subtitles. Avidemux didn't work for me.  Instead I used mencoder.

To install mencoder:  

```
sudo apt-get install mencoder
```

Then I made copies of the originals and put them to a new folder, then opened terminal and used cd command to get to that folder, then:

```
mencoder video_file.flv -sub subtitle_file.srt -oac mp3lame -ovc x264 -o destination_file.avi
```

and voila, the subtitles are hardcoded.

---

