---
title: "How to convert mpeg4 nuv to avi without reencoding"
date: 2008-12-27
forum: Mythbuntu
---

### Post by EasyRiderOnTheStorm on 2008-12-27
NOTE1: Forumites with 'prose'-digesting-issues kindly step away now from this topic instead of taking offense of 'prose'-like content presence below. Thank you.

I'm recording with a framegrabber card, as RT-JPEG nuv. That's fine for everything I record to watch once. Whatever I'd like to keep, I need to compress, and the mythtv "transcode" option is a nice way to do that (into MPEG4 nuv, that's the only other option in the transcoder setup). And then what? I don't want to burn disks, and nothing and nobody outside myth uses nuv (yes I know about dsmyth; no dice - I want something that's **actually** outside-the-rabid-fan-base-and-in-the-real-world portable). On top of that, I'm already MPEG4 encoded in the nuv (which in itself takes as long as the show itself) and re-encoding, again, just to get an avi file sounds like a lot of wasted time and image quality.

NOTE2: YES, I know I'm about the 1.567.346.987.113.797.212-th guy on the net who finds mythtv's nuv-fetish annoying and would just like a simple way to get an avi from a nuv once in a while, but I have yet to see **one** satisfying answer to the 1.567.346.987.113.797.212 questions I've found. Please let me explain:

- MythTv itself lists the following under "Transcoding Out Of nuv":

[LIST]
[*]nuvexport : As far as I can tell, it was never meant to work without re-encoding. Also, it seems like a highly interactive script, I'm not sure it can work without user input.

[*]mythnuv2mkv : Same as the above, it tries to re-encode. Also, I had audio sync slipping in time even in spite of the total re-encoding it did (note: on my 2.66GHz Celeron it takes **several times** the show's length to re-encode it this way, with default settings; I'm not amused)

[*]nuv2avi : The guy who wrote it seemed to have the exact same gripe as me here; unfortunately, it seems to be unmaintained since 2004 (!) and I'm unable to compile it under mythbuntu. Also, I gather it has audio sync issues as well.
[/LIST]

Most answers found refer to one of these options (except the one referring to repackaging with 'mencoder', which seems to suffer from non-seekability in spite of -forceidx and, you guessed it,  audio sync issues), or simply state the dumbness of what said 1.567.346.987.113.797.212 idiots would so much like to do.

In short: I'd like to start with a MPEG4 nuv (or a RT-JPEG one), and end up with an audio-correct MPEG4/xvid/divx avi, via a user job accessible from the front-end menu. Database update is not a requirement (I don't mind the new file going directly to the Video area) but would be nice.

I've given up hope of googling up the answer. If you happen to have it, please, please share... :(

---

### Post by EasyRiderOnTheStorm on 2008-12-30
bump...

---

### Post by bkortleven on 2009-02-13
I found something that might do the job:

Original message found here: [http://www.terrencemiao.com/Webmail/msg00901.html](http://www.terrencemiao.com/Webmail/msg00901.html)

The line you need is:

mencoder -oac mp3lame -ovc lavc -lavcopts vcodec=mpeg4:vstrict=1:vhq:keyint=0:vbitrate=750 -vf scale=1024:576,lavcdeint -endpos 1500 -ffourcc DX50 -o "Name_For_The_AVI_File.avi" Original_NUV_File.nuv

mencoder can be tweaked, but I use the command as is, no problems...

---

### Post by Anubis on 2009-07-05
I wonder how would I convert a whole directory of .nuvs?

My script-foo is nonexistent.):P

---

