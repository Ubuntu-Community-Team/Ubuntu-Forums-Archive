---
title: "my first time using avconv. please advise."
date: 2012-11-25
forum: Multimedia Software
---

### Post by zander1013 on 2012-11-25
hi,

i am trying to use avconv for the first time to convert .ogg audio files to .mp3 files.

in the past i have done this using winff with no problem but for some reason there is not output when i try to convert and a terminal pops up urging me to use avconv instead.

is there a gui interface for avconv?

if not can you please give me the general form of the command line to convert allot of albums in different directories?

i realize i may have to do each directory one at a time.

thank you for the help.

---

### Post by ron999 on 2012-11-25
> **zander1013 said:**
> in the past i have done this using winff with no problem but for some reason there is not output when i try to convert and a terminal pops up urging me to use avconv instead.

Go ahead and use WinFF, ignore the dumb message. :P

---

### Post by zander1013 on 2012-11-25
winff reports libmp3lame cannot be found.

i tried uninstalling winff then re-installing it but i get the same error.

---

### Post by ron999 on 2012-11-25
> **zander1013 said:**
> winff reports libmp3lame cannot be found.

It probably needs the extra codecs.
Try this command:-
```
sudo apt-get install libavcodec-extra-*
```

---

### Post by evilsoup on 2012-11-25
WinFF *is* a frontend for avconv (well, strictly speaking it's a frontend for ffmpeg, but in Ubuntu 'ffmpeg' just links to avconv).

> Go ahead and use WinFF, ignore the dumb message.These are words of truth. But if you want to use avconv (as always, command-line options are faster & more adaptable... once you get past the relatively steep learning curve)...

Basic usage is
```
avconv -i <input options> input <output options> output
```In your case
```
avconv -i input.ogg -c:a libmp3lame -q:a 4 output.mp3
```
will give you an MP3 file with a variable bit rate in the 140-185 kbits/second range; for a higher quality use a lower -q:a number. [This]("http://ffmpeg.org/trac/ffmpeg/wiki/Encoding%20VBR%20%28Variable%20Bit%20Rate%29%20mp3%20audio") page has a brief guide to encoding MP3s (just replace 'ffmpeg' with 'avconv', they're the same for most practical purposes). Of course, encoding from one lossy format (Ogg Vorbis) to another (MP3) is not ideal, you should use a lossless (WAV, FLAC, and a few others) source when possible.

To do every file in a directory, you should use a *for* loop.
```
for f in *.ogg; do avconv -i $f -c:a libmp3lame -q:a 4 ${f/%ogg/mp3}; done
```This will convert every file ending in '.ogg' to an MP3 file, while leaving the originals in place. Change the -q:a option if you want... I'd check out the quality on a single file, then see what you want to do.

---

### Post by zander1013 on 2012-11-25
that line solved the problem.

thank you!

---

### Post by zander1013 on 2012-11-25
@evilsoup,

thank you for taking the time to spell out the avconv command line for me. that was in fact the answer to the question i originally asked.

:popcorn:

---

