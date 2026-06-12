---
title: "Can't erase mp3 id3 tag -- help"
date: 2009-03-13
forum: Multimedia Software
---

### Post by logos34 on 2009-03-13
will someone kindly tell me how to get rid of cover art images on .mp3 files?

e.g.:
> General #0
Complete name                : 02 - Do You Feel Loved.mp3
Format                       : MPA1L3
File size                    : 7.05 MiB
PlayTime                     : 5mn 7s
Bit rate                     : 192 Kbps
Album                        : Pop
Track name                   : Do You Feel Loved
Track name/Position          : 2/12
Genre                        : Folk
**[COLOR="Red"]Comment                      : PANiC Crew[/COLOR]**
ANNO                         : 1997
Artist                       : U2
**[COLOR="Red"]Cover Art (Front)            : Cover Art (Front).jpg[/COLOR]**
Year                         : 1997

Audio #0
Codec                        : MPEG-1 Audio layer 3
Bit rate mode                : CBR
Bit rate                     : 192 Kbps
Channel(s)                   : 2 channels
Sampling rate                : 44.1 KHz
Resolution                   : 16 bits
Writing library              : Xing (new)

> $ eyeD3 02\ -\ Do\ You\ Feel\ Loved.mp3

02 - Do You Feel Loved.mp3	[ 7.05 MB ]
--------------------------------------------------------------------------------
Time: 5:08	MPEG1, Layer III	[ 192 kb/s @ 44100 Hz - Stereo ]
--------------------------------------------------------------------------------
**ID3 v2.4:**
title: Do You Feel Loved		artist: U2
album: Pop		year: 1997
track: 2		genre: Rock (id 17)



I can't seem to get rid of the comments and images/cover art (which persists in showing icon "PANic Crew").

I just want to clear the tags--tried eyeD3, mp3tag, Amarok, Easytag, etc. to no avail.

---

### Post by pickarooney on 2009-03-13
[b]sudo apt-get install id3v2
id3v2 -D $filename[/b]

Works for me. Assuming you have write permissions on the file.

---

### Post by logos34 on 2009-03-13
EDIT:

nm, I think I managed it.  Idv3 seemed to do the trick where the others failed.

thanks picarooney

---

### Post by logos34 on 2009-03-14
Bizarre...thought I had it fixed, but as I was finishing up batch tagging the tracks in Amarok with album title and artitst, it just locked up when it got to the 4th song...had to restart the machine...Same thing when I tried to edit each one individually...it just chokes.  

Jeez what is in those tracks...

---

