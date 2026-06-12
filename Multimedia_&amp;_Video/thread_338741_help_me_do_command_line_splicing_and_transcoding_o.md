---
title: "help me do command line splicing and transcoding of mp3 files"
date: 2007-01-14
forum: Multimedia &amp; Video
---

### Post by ChrisC on 2007-01-14
Hello all -

I've done some poking around here and most of the howto/FAQ posts here are about interactive *graphical* ways to do this.  I want to string together some commands to do this because it's a show (podcast) that I do every month and I want to streamline the process.

I have four mp3 files, call them A.mp3, B.mp3, C.mp3 and D.mp3.  I want to concatenate them together, so that I get one long ABCD.mp3 file, and then I want to transcode them down to a lower bitrate.  The original files are at 128 kbps and I want to crank them down to 64 kbps.  The final file should be around 50 MB in size.  I'd like for the highest quality encoding, meaning that the CPU should work as hard as it can to encode the audio within the 64 kbps constraint.

So, two questions:
1) Can I just concatenate the files together with "cat"?  Do I need a special binary switch?  There's nothing in the man/info pages about that.
2) How to transcode the resulting file?  I'm OK with a two step solution that decodes to WAV and then encodes to mp3.  I just want the highest quality effort all the way.

Bonus:  there typically will be a minute or two of audio at the beginning of the first chunk, and at the end of the last chunk, that I will want to trim off.  It would be great if I could find a way to do that *without* having to load the file into an editor, do yet another decode/encode cycle, etc.  Are there any command line programs for trimming a specific amount of time off an mp3 file?

Thanks!

---

### Post by ChrisC on 2007-01-15
bump ...

---

### Post by ChrisC on 2007-01-17
buuuump ....

---

### Post by majoridiot on 2007-01-17
doing what you describe from the command line isn't possible with out-of-the-box linux
commands, without having to write some pretty sophisticated scripts.

_cat_ wouldn't work in this case as it just aggregates the contents of the files as
you state but the data in those files also include non-musical info such as headers, 
possibly mp3 tags, etc.  which will really mess things up.

if it were me, i would use lame to convert the mp3s to wav and a script to concantenate the
wave files properly.  once you do that, you could use lame (or the encoder of your choice) to
encode the joined waves and compress them to suit your needs.

i've seen the wave concatenation script just recently and lame is probably already on your 
system.  if not, you can apt-get it.

---

### Post by idur on 2007-02-19
mpgtx should be able to do what you want. At least from the man page. There is a debian package for SID so maybe there is one for ubuntu as well.

---

### Post by ChrisC on 2007-07-04
Ooooh, killer, thanks!

---

