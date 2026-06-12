---
title: "videos upside down"
date: 2016-11-19
forum: Multimedia Software
---

### Post by UncleMonty on 2016-11-19
I'm attempting to add subtitles to mov. files (which were recorded on a iPad Air). I've tried Gnome Subtitles and Gaupol Subtitle editor, but every time I add a video it is upside down. Anything I can do to rectify this?

---

### Post by TheFu on 2016-11-20
.MOV is just a container. Which audio and video codecs are used inside it?

Lots of options, but it isn't clear what is upside down - the subtitles or the video?  Do you want to burn-in the subtitles or keep them as SRT data that users can choose to display or not?  Is there a specific "container" that you want to use?  I'd use mkv, because it is the most flexible, but that doesn't help if the playback devices are so old they don't support it.  Is there a specific video codec you need to support? Same for audio - is there a specific audio codec required?

You can transcode the video and rotate it or flip it, if you like.  That will slightly lessen the quality.  Advanced video players can flip/rotate video files based on hints in the metadata, but not all can.  If you want to support any player made in the last 10 years, there isn't much choice for container, audio, and video.  If players are 5 yrs old, it gets a little easier. If players are 1 yr old, you have even more capabilities and choices.

So ... what do you need and what do you ideally want?

The transcode and transform answer is to use ffmpeg/avconv to rotate the video.  There are longer answers based on captioning (SRT) or subtitles (SUB) choices.

---

