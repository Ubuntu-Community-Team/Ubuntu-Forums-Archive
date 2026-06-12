---
title: "Rippng CD to MP3 gives abnormally low bitrate"
date: 2011-03-18
forum: Multimedia Software
---

### Post by gabriella on 2011-03-18
Heres my problem. Maybe someone can tell me whats going on?

I had some problems with ripping CD reacks to MP3 with Asunder. 
I selected Variable bitrate at the highest quality setting. But when I looked at the properties of the files I found that all the tracks reported a bitrate of 96 kbps. This was odd I thought since I've used Asunder before and with VBR the average bitrate varied but was typically around 220.

So I tried ripping using Sound Juicer (Audio CD Extractor) and then Rubyripper. Again the same result with -everyone- of the tracks reporting as 96 kbps. 

Does anyone have any idea whats going?
Thanks..

---

### Post by nickleboyblue on 2011-03-18
Have you tried simply ripping the CD tracks as they are, then converting them?  Also, I highly recommend Sound Converter from the repositories.  It's easy, graphical, and I've never had a problem with it.  Anyway, I might be wrong, but I think maybe your computer is just having a hard time ripping and encoding at the same time.  Try loading the tracks onto your hard drive without changing them at all first, then convert them.  See what happens... probably nothing, but it's worth a shot.

---

### Post by gabriella on 2011-03-18
> **nickleboyblue said:**
> Have you tried simply ripping the CD tracks as they are, then converting them?  Also, I highly recommend Sound Converter from the repositories.  It's easy, graphical, and I've never had a problem with it.  Anyway, I might be wrong, but I think maybe your computer is just having a hard time ripping and encoding at the same time.  Try loading the tracks onto your hard drive without changing them at all first, then convert them.  See what happens... probably nothing, but it's worth a shot.

Hi..

That doesn't seem to make any difference. I should point out I have previously ripped on this PC with the same ripper(s) without any problem.
So I don't get it why now? It's the  same whatever ripper I use. 

Of course whether they really are at 96kbps or just being reported incorrectly I don't know..? I suspect though they are much higher than 96 kbps based onthe file sizes

---

### Post by Schrute Farms on 2011-03-19
I think they are being reported incorrectly.  I have a buttload of cd that were ripped into a VBR format, and a lot of them will report abnormally low bit rates, but if you listen to the files it's obvious that they are actually at a higher bit rate.
MP3s ripped at 96 kbps will sound horrible, especially the cymbals (they seem to take on more of a jingly sound).  If they sound fine, don't worry about it.

---

### Post by StephenDavison on 2011-03-20
One of my computers running Ubuntu starting doing the same thing after installing updates in the first week of March ([http://ubuntuforums.org/showthread.php?t=1701041](http://ubuntuforums.org/showthread.php?t=1701041)). My other computer doesn't have this new behavior and it has all the same updates except for the kernel firmware.  Nevertheless, the files do seem to be encoded correctly.

---

### Post by gabriella on 2011-03-20
> **Schrute Farms said:**
> I think they are being reported incorrectly.  I have a buttload of cd that were ripped into a VBR format, and a lot of them will report abnormally low bit rates, but if you listen to the files it's obvious that they are actually at a higher bit rate.
MP3s ripped at 96 kbps will sound horrible, especially the cymbals (they seem to take on more of a jingly sound).  If they sound fine, don't worry about it.

> **StephenDavison said:**
> One of my computers running Ubuntu starting doing the same thing after installing updates in the first week of March ([http://ubuntuforums.org/showthread.php?t=1701041](http://ubuntuforums.org/showthread.php?t=1701041)). My other computer doesn't have this new behavior and it has all the same updates except for the kernel firmware.  Nevertheless, the files do seem to be encoded correctly.

OK thanks...

I have to say that the tracks sound fine so I guess it's likely a reporting issue.

I did a bit of googling around and found a number of hits on similar issues, inconsistancy in reporting both kbps and track length. Most complaints seem to be from a couple of years back or more but seems as there might be some bugs in the reporting part of the process at least then.

---

### Post by gabriella on 2011-04-02
I think the tracks sound fine that is? It's a little difficult comparing the track played from CD on my stereo to the MP3 player with ear buds.

But someone suggested I try Rubyripper. Well yes that gives a "perfect"  copy and takes a LOT longer to rip a CD but the same reporting error exists when I look at the properties of the ripped file. All around 90kbps. I wonder where the problem to this really lies then?

I presume they would sound like c*** if they really were 90kbps. But I have to say I'd feel more comfortable if I did get the "real" kbps reported..

---

### Post by ron999 on 2011-04-02
Do the math.
Divide the number of bits in the file by the number of seconds duration.

EDIT
That will tell you the _Average_ bit rate for the file.

---

### Post by wolfen69 on 2011-04-02
My favorite open source cd ripper is [CDEX]("http://prdownloads.sourceforge.net/cdexos/cdex_151.exe?download"). It is windows only, but works perfectly with wine installed. I get the maximum bitrate of 320kb with it.

---

### Post by gabriella on 2011-04-02
> **ron999 said:**
> Do the math.
Divide the number of bits in the file by the number of seconds duration.

EDIT
That will tell you the _Average_ bit rate for the file.

I didn't know you could do this but it makes sense now you mention it. Is this really accurate of the what happened during the rippy/encoding?

Anyway wouldn't I have do divide the file size in bits by 1024 to give kilobits first?

So my math is:
File length: 248 secs
File size: 7.2 MB  / 7582007 bytes, 
= 60656056 bits
divided by 1024 = 59234.4 kilobits

59234.4 kb's divided 248 secs = 238 kbps average bit rate.

So is this reasonable given the file was ripped vbr at the highest quality setting?

---

### Post by ron999 on 2011-04-02
> **gabriella said:**
> 238 kbps average bit rate.

So is this reasonable given the file was ripped vbr at the highest quality setting?
Hi
Yes, that seems reasonable to me.
In some places it will use a low bitrate and in other places it will use a high bitrate.
Depends on the music. That's how variable bitrate works.
You've calculated the average for that track.
If you calculate another track, you'll probably get a slightly different answer.

So, I agree, the 96 Kbps is a reporting error.
:D

---

### Post by gabriella on 2011-04-03
> **ron999 said:**
> Hi
Yes, that seems reasonable to me.
In some places it will use a low bitrate and in other places it will use a high bitrate.
Depends on the music. That's how variable bitrate works.
You've calculated the average for that track.
If you calculate another track, you'll probably get a slightly different answer.

So, I agree, the 96 Kbps is a reporting error.
:D

OK thanks. Yes I done a few and all fall in the low 200 kbs range so looks like they're OK. :)

Googling around it seems that others have had a reporting error too, cause though remains unknown.

---

