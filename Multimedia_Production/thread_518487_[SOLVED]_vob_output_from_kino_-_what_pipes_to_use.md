---
title: "[SOLVED] vob output from kino - what pipes to use?"
date: 2007-08-05
forum: Multimedia Production
---

### Post by summersab on 2007-08-05
Alright, so I have it almost figured out. I have been capturing VHS to raw DV via Kino. Now, I am trying to export the video to a vob file for DVD image creation. Under the MPEG tab of Kino's export section, I looked at the advanced options. The lines need tweaking. I found out that for US folk, the audio encoding should be ffmpeg ac3 format, so ffmpeg is used in that line. For the video pipe, I am trying to export to DVD-compatible MPEG2, so, from the manpages of mpeg2enc, I inputted mpeg2enc -v 8 (also tried mpeg2enc -v -f 8 ). For the multiplexer, from the man pages, I discovered that the option "8" is also to be used for DVD purposes, so I used the option mplex -v 8 (also tried -f option). Alright, all that said, the audio export works like a charm. However, the video and multiplexer pipes do not work. The video does not render a file, and with no file, the multiplexer has nothing to multiplex. Formats 0-2 work for mpeg2enc, but above that, none of the options work (3-9). What in the world do I need to put in these lines for Kino to export a MPEG2 AC3 VOB file?

---

### Post by dabl on 2007-08-07
I think you're closer to figuring it out than this noob -- I'm very interested to hear the secret formula, if it is to be revealed.

I captured from VHS tape through a PVR-150 card, which gave me a mpeg2 file (.mpg).  I was trying to work with that file last night, with Kino, and I was able to do splits and cuts to get rid of black sections, noisy sections, and then to re-join the good stuff back into a single file.  But then when I attempted to re-save that edited file, the nightmare began.  It's a big file, so my 4 or 5 attempts to save it took an hour each time.  I tried AVI-1, AVI-2, raw DV, mpeg2, mpeg1, and then gave up and closed it, losing my editing work.  :(

Every time I attempted a save, I got an error at the END of the process.  Usually the error message was suggesting that there might be a problem with the file name.  But, I followed the instruction to enter a path and file name without the extension, assuming Kino would apply the extension.

I dunno -- any clues ?

---

### Post by eggdeng on 2007-08-07
> I followed the instruction to enter a path and file name without the extension
Could be a permission problem with the folder you are saving to. I always give a filename with no path so kino saves under the home folder. Another possibility is that you might be using an illegal character,(é) or something, in the filename.

---

### Post by dabl on 2007-08-07
> **eggdeng said:**
> Could be a permission problem with the folder you are saving to. I always give a filename with no path so kino saves under the home folder.

Good idea -- I'll check permissions on the partition/folder I'm using.  But I can't use /home -- these files are too big for the space left in my /home partition.

>  Another possibility is that you might be using an illegal character,(é) or something, in the filename.

Another good idea, although I think I'm down to standard ASCII alphanumeric characters at this point.

Thanks for the ideas! :)

---

### Post by summersab on 2007-08-11
bump for the ORIGINAL question - anyone?

---

### Post by dad311 on 2007-08-14
I have done this to 20-30 home movies.  Did you try the "other" tab under export?

I always use the following settings under Export-Other:

Tool: DVD-Video Dual Pass (FFMPEG_
Profile: Standard VOB

---

### Post by summersab on 2007-08-17
You know when you have one of those "DUH" moments? Yeah - I just had one. Wow, thanks for your reply. That tab does everything flawlessly. Imagine that. And I was just going to test out my scripting skills with smil2yuv, mpeg2enc, and mutiplex. Too bad . . .

---

