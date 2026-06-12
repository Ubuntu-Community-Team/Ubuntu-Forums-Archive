---
title: "VLC: Soft-Sub issues"
date: 2007-12-22
forum: Multimedia &amp; Video
---

### Post by NamedUser on 2007-12-22
The source of my problem is a simple .mkv file. The video plays, fine, I can select the subtitle track, and the subtitles even display... except that they display in FRICKIN HUGE font  no matter what I set it to display at! I tinkered with settings for a while, but I couldn't get the subtitles to display at a reasonable size (which I have been able to do with other .mkv files that had soft-subs). Not only that, but I can't even get the file to do anything but crash the other players that I've tried!

SOLUTION:
Open Settings -> Preferences
Navigate to Input/Codecs->Other codecs->Subtitles
Uncheck "Formatted subtitles"

Why this isn't under the Video->Subtitles options menu, I don't know, but there you have it. If the subtitles in a soft-subbed video display way to big (or too small, I suppose) and don't respond to resizing, there's your answer.

---

### Post by NamedUser on 2007-12-22
Well that memory leak problem went away, but I still have the original problem. Even when other mkv files listen to the settings, this one .mkv I have ignores all attempts to make the subtitles a reasonable size.

---

### Post by NamedUser on 2007-12-22
Hmm.. I take it by the lack of response that no-one is gonna help me with my subtitle issue? Bah.

---

### Post by MaindotC on 2008-03-16
Not working out that way for me :(

---

### Post by MaindotC on 2008-03-18
Ok, I did change the font size but only by doing: "Open File" (as opposed to Quick Open File), selected the video file and then selected the corresponding subtitle file.  When I selected the subtitle file, I could only set the "Relative Font Size" to small or smaller - both of which helped but still some subtitles were off the screen.  I left-justified them which also helped.

Thanks for pointing me in this direction.

---

