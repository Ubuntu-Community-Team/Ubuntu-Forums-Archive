---
title: "Ripping CD to mono mp3 in SoundKonverter"
date: 2007-05-04
forum: Multimedia &amp; Video
---

### Post by mjpatey on 2007-05-04
Hi, folks-

I'm using SoundKonverter in Feisty to rip my pastor's sermons from CD to mp3 format to post on our church's Web site.  In the past (before I switched to Ubuntu), the software I used gave me a lot of easily-accessible control over the exact parameters of the conversion.

Right now, in SoundKonverter, I've hit a little speed bump.  I'm trying to rip audio from the CD (recorded in mono, but of course, ripping from CD results in a stereo file regardless), and go directly to a 64Kbps **mono** mp3 file.  I'm able to set it to 64Kbps, but the program assumes stereo, since that's what it sees is coming in.  There appears to be an option to set it to mono in SoundKonverter, but that is grayed out.

The resulting stereo mp3, of course, is at half the sound quality because at 64 Kbps, it uses 32 Kbps for each channel, rather than the whole 64Kbps for a single channel.

The only clue I have is under "Advanced Options", it has a field for "Command", which currently displays:

> /usr/bin/ffmpeg %p -i %i %o

It gives me the option to type into this field; is there some magic command I can insert into that text that would specify a mono mp3?

Sorry if my post is confusing, and thanks for any help you may be able to provide!

-Mark

---

### Post by stchman on 2007-05-08
> **mjpatey said:**
> Hi, folks-

I'm using SoundKonverter in Feisty to rip my pastor's sermons from CD to mp3 format to post on our church's Web site.  In the past (before I switched to Ubuntu), the software I used gave me a lot of easily-accessible control over the exact parameters of the conversion.

Right now, in SoundKonverter, I've hit a little speed bump.  I'm trying to rip audio from the CD (recorded in mono, but of course, ripping from CD results in a stereo file regardless), and go directly to a 64Kbps **mono** mp3 file.  I'm able to set it to 64Kbps, but the program assumes stereo, since that's what it sees is coming in.  There appears to be an option to set it to mono in SoundKonverter, but that is grayed out.

The resulting stereo mp3, of course, is at half the sound quality because at 64 Kbps, it uses 32 Kbps for each channel, rather than the whole 64Kbps for a single channel.

The only clue I have is under "Advanced Options", it has a field for "Command", which currently displays:



It gives me the option to type into this field; is there some magic command I can insert into that text that would specify a mono mp3?

Sorry if my post is confusing, and thanks for any help you may be able to provide!

-Mark

I have a procedure to download the codecs and configure Sound Juicer to rip your audio CDs to MP3s using the LAME encoder for VBR.

[http://www.stchman.com/cd_rip.html](http://www.stchman.com/cd_rip.html)

You can try changing the channels=2 to channels=1.  I have never tried this myself.  Since your pastor's sermon will probably just be him speaking the VBR coding of LAME will give you small file size. 


It works.

---

