---
title: "Combining Videos - is it possible?"
date: 2010-06-28
forum: Multimedia Software
---

### Post by ytaews on 2010-06-28
I am trying to combine two videos into one file, so that I can have them playing side by side and in sync. Basically they are two angles of the same thing, and I want to be able to demonstrate both at once. The files are completely different formats right now (MPEG-2 and h.264), but I could convert them. Is there any way to do this, or a way I could have them both play in sync even if I can't combine them?

Thanks.

---

### Post by ytaews on 2010-06-30
Anyone? The best I have so far is opening up both clips in VLC and doing a screen recording of both

---

### Post by Spinoza on 2010-09-16
A few possibilities exist.

1.) [http://en.wikipedia.org/wiki/Cinelerra](http://en.wikipedia.org/wiki/Cinelerra)  if you can get it to not crash too much.

2.) Maybe Kino. I am not 100% sure it does side by side combining.

3.) Export each video to a set of image files in their own directory, one per frame with ffmpeg. Then use ImageMagick tools (convert?) to combine each equivalent frame into a single image in a third directory. Then encode those into a video with ffmpeg.

I've done a bit of research on this myself. I'm looking for a method of combining four 320x240 video streams into a single 640x480 stream. However, none of these methods can work for me ( except maybe the last one modified a bit ) because I need to do it with live video from 4 cameras, in real time, with less then 5 seconds of latency.....

---

