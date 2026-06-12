---
title: "How to specify subtitle color in video"
date: 2022-07-04
forum: Multimedia Software
---

### Post by py-ohayo on 2022-07-04
Hello,

There are 3 ways to play a video with subtitles:
[LIST]
[*]hard embedding: this method involves rendering subtitles into particular frames, time-consuming process, requiring intensive processing
[*]soft embedding: fairly fast method, subtitles are embedded as metadata in the video file, then during playback smart video players (not all!) render the subtitles in particular frames
[*]do not embed any subtitles, just keep the subtitle file which can be read by smart player while the video is playing
[/LIST]

The 2nd method appears to be the most effective because on the one hand it allows rapid processing on the other hand it avoids keeping two files (or more in the case of several languages) - video and subtitles.
The only issue with the 2nd method - there is no possibility to change subtitle color.
In VLC player, this option exists, but seems not to work... at the same time, changing font works.
In another player "Videos" there is no option to work with subtitles... only enable them.
There's probably a dedicated option somewhere in the Ubuntu staff?
Thanks.
Sincerely,

---

### Post by Xian on 2022-07-04
What is the text format being used .... ?

---

### Post by py-ohayo on 2022-07-05
If I correctly understood your question ...
The original subtitle file is .vtt.
In order to embed subtitles into video using ffmpeg I have first to convert it to .srt.

---

### Post by SeijiSensei on 2022-07-05
If you find a reliable method of converting from VTT to SRT, please post it here. I looked at a number of solutions over the weekend and came up empty.

With an SRT file, you can add a subtitle color by following the method described here: [https://ubuntuforums.org/showthread.php?t=2328454&p=13507429&viewfull=1#post13507429](https://ubuntuforums.org/showthread.php?t=2328454&p=13507429&viewfull=1#post13507429) Notice the weird color codes.

---

### Post by py-ohayo on 2022-07-06
Here is the tool that do conversion vtt --> srt:
[https://subtitletools.com/convert-to-srt-online](https://subtitletools.com/convert-to-srt-online)
As for your method, it **burns** the subtitles into the video which takes a lot of time.
I'm looking for a method to **embed** subtitles (not **burn** them!) and then change color in player...or change color while embedding.

---

