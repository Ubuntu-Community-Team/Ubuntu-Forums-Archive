---
title: "adjusting subtitles on mencoder"
date: 2008-04-30
forum: Multimedia Software
---

### Post by DarchAengel on 2008-04-30
I looked around the older posts and can't seem to find anything quite as similar as my problem.  I am hard subbing avi files that I converted from mkv files.  I am using mencoder and the problem is that the subtitles are so big and obnoxious.  I was hoping someone could tell me the commands/syntax for adjusting the size, font, color, etc of subtitles when using mencoder.

---

### Post by little_penguin on 2008-05-02
I'm sure there are various ways to do this, but this is what I do:

AFAIK mencoder uses a default subtitle size of 5%, which to me is a bit too big and you can reduce it via -subfont-text-scale 

For example I use the following:

-subfont-text-scale 3

The possible settings for the size are 0 - 100, where this represents the font as a percentage of the screen size.

For the actual font used, I have a file called subfont.ttf in my .mplayer directory (under home). Concrete example: you can copy Verdana.ttf (/usr/share/fonts/Truetype), or any other truetype font you want, to this .mplayer directory under your home dir and rename it to subfont.ttf. This font will then be used in your subtitles.

I'm not sure about changing the color, perhaps someone else can help there, as I'm just a newbie myself :o)

---

