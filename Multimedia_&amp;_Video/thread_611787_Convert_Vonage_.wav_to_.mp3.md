---
title: "Convert Vonage .wav to .mp3"
date: 2007-11-13
forum: Multimedia &amp; Video
---

### Post by pug2694328 on 2007-11-13
I've configured my Vonage VOIP service to forward voicemails to my email address.  They come with a .wav suffix, but in actuality they're compressing them down using CCITT u-Law rather than standard .wav.

I'd like to convert these CCITT u-Law .wav files to .mp3, but am not meeting with success yet.

I've found this site:
[http://blog.pumacode.org/2006/05/14/converting-vonage-voicemails-to-mp3/](http://blog.pumacode.org/2006/05/14/converting-vonage-voicemails-to-mp3/)

It gives a good description of the problem, but the code is above my head.

I have both sox and lame, lame can't handle the CCITT u-Law format, but sox supposedly can.
Does someone know the correct BASH command for converting this format to .mp3 via sox?

I've attached a sample input file.

---

### Post by timcredible on 2007-11-13
don't know about sox, but ffmpeg may do that conversion - might want to check the options for it, ffmpeg is in synaptic

---

### Post by pug2694328 on 2007-11-13
Okay here's how to do it:

sox <input file> -t wav -s -w - | lame - <output file>

For those new to bash (me!) this code uses the program sox to pipe output to the program lame.
The - is in lieu of a filename, it's 'standard output' (or 'standard input for the lame program').

Read the man entries of each program to get more info.

It works!

---

