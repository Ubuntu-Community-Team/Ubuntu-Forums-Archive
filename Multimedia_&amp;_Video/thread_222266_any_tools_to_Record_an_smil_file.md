---
title: "any tools to Record an smil file?"
date: 2006-07-24
forum: Multimedia &amp; Video
---

### Post by kline on 2006-07-24
Given that I have a URL that points to an smil file, is there any tool that will let me record this file?  and hopefully convert it to some default, like mp3??  If not convert, them at least record?

---

### Post by kline on 2006-07-31
Well, after a couple days, and asking elsewherre, and wasting--or spending--at least ten hours trying to capture an NPR smil file, I finally googled and found the following Linux snippet.  

As one fellow on the -questions list on FreeBSD suggested: you need to hack up the .smil file before you cn do anything with it.  True.  So I saved the files to /tmp, edited away the garbage, and applied the follow mplayer -STUFF.  Works beautifully.

[B][I][CENTER]
mplayer -noframedrop -dumpfile out.rm -dumpstream  \
rtsp://url/to/file.rm[/CENTER][/I][/B]

Now, anybody who wants to, can save any smil or *.rm fil with mplayer.  I have a follow-up a question for any of the audio wizards out there.  Can I convert the *.rm files to DOS *.wav format, and then turn the *wav files into *.mp3 files...??

---

### Post by csrster on 2007-03-28
Yes! once you've got your .rm file, converting to an mp3 is trivial with ffmpeg,
e.g. 
>ffmpeg -i infile.rm outfile.mp3
will do it. Use the -ab option to specify a bitrate. 

--
Csrster

---

