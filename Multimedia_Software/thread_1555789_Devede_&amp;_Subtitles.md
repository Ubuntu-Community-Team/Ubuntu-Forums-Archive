---
title: "Devede &amp; Subtitles"
date: 2010-08-18
forum: Multimedia Software
---

### Post by Stigmata13 on 2010-08-18
Hello. I've recently decided to burn a dvd with a few episodes of an anime show on them, and it's worked fine except one small problem.
The anime episodes are in .mkv format with .a$$ subtitles within the container (replace $ with s)
Originally burning the dvd, everything went fine although the subtitles were ugly and far too big. Parts with a lot of dialogue frequently caused letters or even whole words to be cut off on the left or right side of the TV screen.
I tried using the options to change size from within DeVeDe but at first it wouldn't work, since the subtitles were within the MKV container. DeVeDe didn't seem to see them, yet would load them and put them on just fine (aside from the massive size.)
Anyway, I found I could use mkvextract to extract the video, audio, and subtitle tracks, and then use mkvmerge to put the audio/video back in an .mkv container, leaving me with an external subtitle file I could load into DeVeDe, but here's where I ran into problems. DeVeDe doesn't seem to want to implement the subtitles in the way they are specified, and in fact shows them in a strange way, the center of the text being transparent with a white border.

Here's what the subtitles **should** look like: 

[IMG]http://www.freeimagehosting.net/uploads/07998efd9c.png[/IMG]

And here's the way DeVeDe attempts to style them:

[IMG]http://www.freeimagehosting.net/uploads/15ec95ee9a.png[/IMG]

Sorry for the small image for the first pic, it was taken from within Aegisub, the program I used to style the subtitles.

I think this has something to do with SPUMUX, the way DeVeDe interprets subtitles for burning. Can anyone give me any hints on how I can fix this problem and make them appear the way they should?\

Edit: Sorry if the images are hard to see. I used a free image hosting site to upload them and it seems that it resized them. The top image has FreeSeriff size 20 font, white with a black border. The Second image however,  the words are transparent with a white border. This is using the same subtitle file in both programs.

---

### Post by Stigmata13 on 2010-08-20
Nevermind, it turns out it's just a bug with the preview, and the fonts display correctly after the dvd is encoded.

---

