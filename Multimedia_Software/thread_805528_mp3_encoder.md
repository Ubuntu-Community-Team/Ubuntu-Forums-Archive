---
title: "mp3 encoder"
date: 2008-05-24
forum: Multimedia Software
---

### Post by hirohitosan on 2008-05-24
Hi there.
In your opinion which is the best mp3 encoder?
thx

---

### Post by accodata on 2008-05-24
I asked the same question a couple of days ago and was told RipOff is ok, however, I found that you can only rip 2 songs at a time, so it is a lengthy process ripping a cd. I also downloaded mp3gain, and that helps as well.

Good Luck

Accodata

---

### Post by amn on 2008-05-24
> **hirohitosan said:**
> Hi there.
In your opinion which is the best mp3 encoder?
thx

According to the many listening tests performed at the Hydrogenaudio forums, it's without a doubt LAME (see quote below). See the [LAME entry in the Hydrogenaudio Knowledgebase]("http://wiki.hydrogenaudio.org/index.php?title=LAME") to find useful information about the settings to use for optimal quality vs. bitrate. Personally I use the "-V2 --vbr-new" setting. LAME is available in the Ubuntu repos.
> **LAME - Hydrogenaudio Knowledgebase]Nowadays LAME is considered the best MP3 encoder at mid-high bitrates and features the best VBR model among MP3 implementations, mostly thanks to the dedicated work of talented developers like Takehiro Tominaga, Naoki Shibata, Darin Morrison, Gabriel Bouvigne, Robert Hegemann, etc. And development is still going on...[/QUOTE]

[QUOTE=accodata said:**
> I asked the same question a couple of days ago and was told RipOff is ok, ...
RipOff is a CD-ripper not a MP3 encoder, though RipOff can use LAME to encode MP3 files. I would recommend the ripper "abcde" (available in the Ubuntu repos), in case your comfortable using the shell.

> **accodata said:**
> I also downloaded mp3gain, and that helps as well.
[MP3Gain]("http://wiki.hydrogenaudio.org/index.php?title=MP3Gain") is an implementation of Replay Gain useful when your player of choice does not support Replay Gain tags.

---

### Post by hirohitosan on 2008-05-24
Thanks guys.
I installed LAME.
Now I tried to copy an audio CD on my computer. I tried with Sound juicer, but at output format is just ogg, flac, wav. How can I add mp3 encoder
thanks

---

### Post by gandaran on 2008-05-24
> **hirohitosan said:**
> Thanks guys.
I installed LAME.
Now I tried to copy an audio CD on my computer. I tried with Sound juicer, but at output format is just ogg, flac, wav. How can I add mp3 encoder
thanks

if you want to rip to mp3 with sound juicer, install the gstreamer ugly multiverse variant plugin or better still, install all the gstreamer plugins, you mite need them sometime.to convert to mp3 other formats install sound converter.

---

### Post by hirohitosan on 2008-05-24
well I installed gstreamer, but still don't know how to rip an audio cd to *mp3
:confused:
In Sound juicer I went at Preferences and try to chose from Format>Output Format mp3  but still not on the list

any help?

---

### Post by gandaran on 2008-05-24
> **hirohitosan said:**
> well I installed gstreamer, but still don't know how to rip an audio cd to *mp3
:confused:
In Sound juicer I went at Preferences and try to chose from Format>Output Format mp3  but still not on the list

any help?

did you install the correct gstreamer plugin?
[http://blog.mypapit.net/2007/05/how-to-rip-mp3-cd-using-sound-juicer-ubuntu-tips.html](http://blog.mypapit.net/2007/05/how-to-rip-mp3-cd-using-sound-juicer-ubuntu-tips.html)

---

### Post by disturbedite on 2008-05-24
i recommend using free (& better) audio formats like ogg & flac.  but if you must have mp3 for certain reasons, lame is prolly the best mp3 coder.

---

### Post by Major_Kong on 2008-05-24
Try to use rubyripper instead of soundjuicer to rip the cds, its more reliable. It uses lame to do the mp3 encoding too. (debs avaliable at getdeb.net )

---

### Post by hirohitosan on 2008-05-25
> **gandaran said:**
> did you install the correct gstreamer plugin?
[http://blog.mypapit.net/2007/05/how-to-rip-mp3-cd-using-sound-juicer-ubuntu-tips.html](http://blog.mypapit.net/2007/05/how-to-rip-mp3-cd-using-sound-juicer-ubuntu-tips.html)
Well I installed gstreamer0.10-plugins-ugly-multiverse, 


Thanks!

Itworksnow

---

