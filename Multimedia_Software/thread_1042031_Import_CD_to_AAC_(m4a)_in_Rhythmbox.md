---
title: "Import CD to AAC (m4a) in Rhythmbox"
date: 2009-01-17
forum: Multimedia Software
---

### Post by phenest on 2009-01-17
I currently have a large music collection in ogg vorbis but I'd like to rip my CD's again but this time to m4a's. Rhythmbox is able to do this but there is no setting for quality and Rhythmbox reports them as 'Unknown' quality. I guess they must be vbr, but surely there must still be a quality setting.

From what I've read, aac is better quality than mp3 or vorbis and you don't need such high quality settings, i.e. 128k in aac is equivalent to 192k in mp3. But what quality setting is Rhythmbox using? And what is a good setting for CD quality?

---

### Post by phenest on 2009-01-17
I've decided Rhythmbox is not a good idea for m4a's. They sound horrid! Maybe gstreamer isn't too hot with encoding m4a's, whereas ffmpeg does a great job of it. Now I need a ripper than can rip to m4a's.

---

### Post by mc4man on 2009-01-17
I use rubyripper with neroAacEnc for ripping/encoding, it works quite well in 8.04. In 8.10, while it works, somethings not quite right.

You could try grip in 8.10 using faac (I'm thinking that's what you have

The default setting in grip is I believe is %b which is a -q of around 100 (not 100% sure, I believe in faac the -q range is 10 - 500

You could change the default encode line to this and then experiment with different values (red

```
-q [COLOR="Red"]250[/COLOR] -o %m -w --artist %a --title %n --genre %G --album %d --track %t/%N --year %y %w

```

I also found grip didn't number the tracks so changed the naming line like this
```
[COLOR="Red"]~/Music[/COLOR]/%A/%d/%t- %n.%x

```
red indicates where to save to, you can use whatever you wish

here's a somewhat rambling thread with additional info (Op was looking for high bitrates, certainly higher than needed i believe

[http://ubuntuforums.org/showthread.php?t=1025034](http://ubuntuforums.org/showthread.php?t=1025034)

---

### Post by phenest on 2009-01-17
I tried Grip but it quits after each track is encoded. Gstreamer and faac produce very bad sounding files, whereas ffmpeg gives very good quality. In fact, I've produced a little bash script:
```
#!/bin/bash

# CD rip to m4a

cdparanoia -B 1-

for i in *.wav; do ffmpeg -y -i $i -acodec libfaac -aq 200 `basename $i .cdda.wav`.m4a; rm $i; done

exit 0
```
I then have to use a tag editor such as Ex Falso as I don't know how to do cddb from bash. But that's not important.

---

### Post by phenest on 2009-01-18
I discovered why m4a files sound bad in Rhythmbox: Edit the profile for aac/m4a and add:

profile=2

into the pipeline, so it reads:

... ! faac profile=2 ! ...

Apparently, gstreamer defaults to profile 1. Someone else might be able to give a technical answer to why this is.

This also applies to Sound Juicer.

---

