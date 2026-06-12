---
title: "what causes audio out of sync?"
date: 2012-09-28
forum: Multimedia Software
---

### Post by qwertyjjj on 2012-09-28
What causes audio to go out of sync on downloaded media?

---

### Post by stagelurkerr on 2012-09-28
There is a good chance it is a frame rate issue. Video calculates in frames per second while audio is calculated by samples per second.  Changing video formats can make minor adjustments to the frame rate of the image.  You may not notice that it is off sync immediately, but over time little differences in audio/video sync become big differences.

Dan

---

### Post by qwertyjjj on 2012-10-28
> **stagelurkerr said:**
> There is a good chance it is a frame rate issue. Video calculates in frames per second while audio is calculated by samples per second.  Changing video formats can make minor adjustments to the frame rate of the image.  You may not notice that it is off sync immediately, but over time little differences in audio/video sync become big differences.

Dan

Well, it's immediately out of sync from the start of the program/video so it's not slowly going out of sync...I slow it down by 0.150s and then it stays in sync for the whole program. What would cause the audio to be coded like that when it is ripped?

---

### Post by VanillaMozilla on 2012-10-29
What a pain.  I suspect somebody goofed badly when they invented these codecs.

There are ways of fixing an offset sync when you import a file into certain video editors, but that's a desperation measure if you ask me.

Try ProjectX.  This often works.  Add the file, then press the "Quick" button to convert it to separate .m2v (video) and .ac3 (sound) files (or whatever you choose).  Then reassemble them in a video editor.

Don't ask me what it does.  It's just black magic.  Just push the button and stand back.  Can be installed from Ubuntu repositories.  If it doesn't work, I can't help you more.

---

### Post by FakeOutdoorsman on 2012-10-29
> **qwertyjjj said:**
> Well, it's immediately out of sync from the start of the program/video so it's not slowly going out of sync...I slow it down by 0.150s and then it stays in sync for the whole program. What would cause the audio to be coded like that when it is ripped?

How do you know it's not your player instead of the source file? Have you used another player? Which one are you using?

---

### Post by VanillaMozilla on 2012-10-29
FakeOutdoorsman, this is a common occurrence with video files, and you'll find lots of references to it across the Web.  Perhaps you haven't used the right file type to experience the problem.

It's seemingly random and capricious.  I've had one player work for one file, while another player works for another file.  You never know what player will work or what editor will work.  It seems to be a problem with certain codecs.  But my experience is that once you fix the file, it works for all.

---

### Post by qwertyjjj on 2012-10-31
> **FakeOutdoorsman said:**
> How do you know it's not your player instead of the source file? Have you used another player? Which one are you using?

using xbmc and most of the other videos play in sync it's just this one season of videos that I downloaded that everything has to be synced back at the start of each episode.

---

### Post by qwertyjjj on 2012-10-31
> **VanillaMozilla said:**
> What a pain.  I suspect somebody goofed badly when they invented these codecs.

There are ways of fixing an offset sync when you import a file into certain video editors, but that's a desperation measure if you ask me.

Try ProjectX.  This often works.  Add the file, then press the "Quick" button to convert it to separate .m2v (video) and .ac3 (sound) files (or whatever you choose).  Then reassemble them in a video editor.

Don't ask me what it does.  It's just black magic.  Just push the button and stand back.  Can be installed from Ubuntu repositories.  If it doesn't work, I can't help you more.

Does it reassemble them automatically or do you have to do that manually?

---

### Post by qwertyjjj on 2012-12-03
Here's the weird thing.
When I play it from my main desktop on xbmc (more powerful), I have to delay the audio by 1.5 secs right from the beginningof the program and it stays in sync for the 1hr episode.
When I play the same episode from a client xbmc on a laptop upstairs (less powerful), it is in sync from the beginning.

?!?!??!

---

