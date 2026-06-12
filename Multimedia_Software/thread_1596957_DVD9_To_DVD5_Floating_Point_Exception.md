---
title: "DVD9 To DVD5 Floating Point Exception"
date: 2010-10-14
forum: Multimedia Software
---

### Post by luangwa on 2010-10-14
I have been trying to convert a DVD9 to DVD5 using the following steps
1)Rip the DVD title(s) to harddisk with DVD:RIP in a project folder. This created VOB files of the the movie and the soundtrack you picked.
2)Concatenate (merge) the VOB files into one by running in a console:

cat *.vob > movie.vob 
3)demutliplex movie.vob and get the M2V and AC3 files out of there. 

tcextract -i movie.vob -t vob -x mpeg2 > movie.m2v 

4)tcextract -i movie.vob -a 0 -x ac3 -t vob > movie.ac3

5)I then shrank the movie.m2v

	tcrequant -i movie.m2v -o shrinked.m2v -f 1.5 

6)Everything seemed to be fine until I tried to multiplex the 2 files into a compliant DVDauthor file:

 mplex -f 8 -o final.mpg shrinked.m2v movie.ac3
And then I get this?
   INFO: [mplex] mplex version 1.9.0 (2.2.7 $Date: 2006/02/01 22:23:01 $)

   INFO: [mplex] File shrinked.m2v looks like an MPEG Audio stream.

   INFO: [mplex] File movie.ac3 looks like an AC3 Audio stream.

   INFO: [mplex] Found 2 audio streams and 0 video streams

   INFO: [mplex] Selecting dvdauthor DVD output profile

   INFO: [mplex] Multiplexing video program stream!

   INFO: [mplex] Scanning for header info: Audio stream c0 (shrinked.m2v)

Floating point exception


How can I fix a floating point exception? Lost:confused:

---

### Post by Yellow Pasque on 2010-10-14
Not sure about the floating-point thing, but I use k9copy.

---

### Post by mc4man on 2010-10-14
> How can I fix a floating point exception?

Well, something sure went wrong somewhere - maybe backtrack thru the various files and see (if you kept them, a fair amount of space used.
Try them all in a video player or ck. in mediainfo

> INFO: [mplex] File shrinked.m2v looks like an MPEG[COLOR="Red"] Audio [/COLOR]stream.
That's what's causing the exception. You'd want to see this instead
> INFO: [mplex] mplex version 1.9.0 (2.2.7 $Date: 2006/02/01 22:23:01 $)
   INFO: [mplex] File shrinked.m2v looks like an MPEG Video stream.
...........
INFO: [mplex] Found 1 audio streams and 1 video streams

if you're just doing a simple requant then am wondering why go to all this trouble, just let an app do. Never used DVD:RIP but I'd imagine it could do as well as several other apps.

---

