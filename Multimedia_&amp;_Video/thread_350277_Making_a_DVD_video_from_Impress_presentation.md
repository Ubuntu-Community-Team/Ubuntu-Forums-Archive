---
title: "Making a DVD video from Impress presentation"
date: 2007-01-31
forum: Multimedia &amp; Video
---

### Post by Coburn on 2007-01-31
I'd like to take a slide-based presentation, add audio, and put it on a CD or DVD so it can be played on a TV where using a computer is inconvenient.   This amounts to a cheap, portable projection system.:guitar: 

There seem to be a few non-free, Windows-based tools out there for doing this sort of thing, but I have a hunch there are ways to do it within the Ubuntu system.

I have GAP, MPlayer, and QDVDAuthor, among other tools, but nothing in the documentation I've read seems to get me from  point A to point B.  Plus my (recently updated on Dapper) version of Impress won't export to XHTML, which I thought might help.:confused: 

Thanks,

Coby

---

### Post by Paerez on 2007-01-31
Here is my way of doing it:

1) Use xvidcast to create a screencast of your presentation. This will create an AVI file.
[http://xvidcap.sf.net/](http://xvidcap.sf.net/)

2) Convert that video to DVD format. QDVDAuthor may do this, I don't know. But you can also use mencoder or ffmpeg.

3) Burn!

If you want to voice-over your presentation, use gnome's sound recorder to record your voice, then you would have to use mencoder or ffmpeg or something to put the audio on top of the video.

Good luck.

---

### Post by Coburn on 2007-01-31
Thanks for the leads.

They led me to look at transcode, which can-do in CLI, but as one guy says:

"These tools were powerful and had all features I needed but it was mind boggling to remember all those command line options and XML tags.  Making even simplest menus required lot of work.  A small mistake somewhere in the process used to cost me lot of time."

To share the results of my search, here is a nice list somebody put together:  [http://forum.doom9.org/showthread.php?t=114966](http://forum.doom9.org/showthread.php?t=114966)

Looks like there are definitely some tools under development out there.  I will report back when I know what works.

---

