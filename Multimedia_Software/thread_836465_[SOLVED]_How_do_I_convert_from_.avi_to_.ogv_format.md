---
title: "[SOLVED] How do I convert from .avi to .ogv format?"
date: 2008-06-21
forum: Multimedia Software
---

### Post by Rytron on 2008-06-21
Hi,
I have tried various times to convert a .avi file to .ogv using OggConvert. I tried both the ogg & matroska file format with the Theora video format settings. I did not use the Dirac video file format as it is still experimental. Every time it finishes converting, I cannot not play the .ogv file as I get an error. It did convert with matroska(.mkv) but I had no sound.
I used OggConvert to successfully convert all my other .avi files to .ogv with ease.
Is there another program that can convert this troulesome .avi file to .ogv for me?
Thanks.

---

### Post by Agent ME on 2008-06-21
Try using VLC, it supports many formats and is great for re-encoding media files. It might not be able to do this exactly but is worth a try.

---

### Post by mastermindg on 2008-06-22
There is a ffmpeg2theora program available in the universe repository. (Theora is the ogg video format.) It's command line, but not hard to use, here you can find some examples: [http://v2v.cc/~j/ffmpeg2theora/examples.html](http://v2v.cc/~j/ffmpeg2theora/examples.html) .

Converting from one compressed format to another may not give best quality.

---

### Post by vauss on 2008-06-22
Hi,
If you want to convert an .avi to .ogv, I created a small frontend (VFFF) for the commandline software ffmpeg2theora : [http://www.vauss.net/vfff.htm](http://www.vauss.net/vfff.htm)
Here is a .deb package in order to easily install my program : [http://www.vauss.net/vfff/vfff_0.98_en_all.deb](http://www.vauss.net/vfff/vfff_0.98_en_all.deb)

---

### Post by Rytron on 2008-06-22
> **mastermindg said:**
> There is a ffmpeg2theora program available in the universe repository. (Theora is the ogg video format.) It's command line, but not hard to use, here you can find some examples: [http://v2v.cc/~j/ffmpeg2theora/examples.html](http://v2v.cc/~j/ffmpeg2theora/examples.html) .

Converting from one compressed format to another may not give best quality.

Hi,
Thank you very much. Your suggested method worked a charm. Very quick too.
Cheers my friend.

---

### Post by Rytron on 2008-06-22
> **vauss said:**
> Hi,
If you want to convert an .avi to .ogv, I created a small frontend (VFFF) for the commandline software ffmpeg2theora : [http://www.vauss.net/vfff.htm](http://www.vauss.net/vfff.htm)
Here is a .deb package in order to easily install my program : [http://www.vauss.net/vfff/vfff_0.98_en_all.deb](http://www.vauss.net/vfff/vfff_0.98_en_all.deb)

Thank you vauss. That is a great frontend. Great thinking.
:)

---

### Post by Rytron on 2009-11-26
The link for VFFF is now broken. Does anyone know of another link?

---

### Post by ilil on 2009-11-26
Winff is a good frontend for converting files with FFmpeg

---

### Post by Rytron on 2009-11-26
Thank you ilil. I use WinFF, however it doesn't seem to convert to .ogv format.

OggConvert sometimes doesn't work but VFFF does the job.

---

### Post by ilil on 2009-11-26
Well, it is good idea to make a Winff preset for OGV and suggest to developers :)

---

### Post by Rytron on 2009-11-27
I contacted [vauss]("http://ubuntuforums.org/member.php?u=536474").

He very kindly provided me with a new link:
[http://www.vauss.net/vfff/vfff_0.99_en_all.deb](http://www.vauss.net/vfff/vfff_0.99_en_all.deb)

Many thanks to vuass.

:P

---

### Post by Robin B on 2010-10-07
I have used VFFF to convert an avi file to ogv format. However, whilst the video worked fine, the audio is garbled, sounding as though it is at double speed. In fact the audio finishes when the video  has only played half way through. Any ideas anyone?

Robin B

---

### Post by Robin B on 2010-10-18
Further to my above post re converting an avi file taken on my digital camera to an ogv file, I have now solved my problem and gained knowledge in the process.

I first tried to make the conversion using the vfff front end. When this did not work, as described in the previous post, I contacted Vauss who has been brilliant, exchanging several emails with me until a final solution was found. 

Initially, after ascertaining it was an ffmpeg problem and not vfff,  we tried to convert using just ffmpeg2theora (at the command line) with various parameters. However, though this did not work, producing ogv files but not ones where the audio and video synced.

The problem turned out to be that my avi files come from my digital camera, the video being encoded in a specific codec, MJPEG, which is a good codec format for digital camera, but it generally causes audio/video sync problem when converted into another video format. 

The solution is in two steps:

Step 1, convert AVI to MPEG file :
Open a terminal and type this command line :
ffmpeg -i theoriginalfile.avi -b 100000k -ab 128k -ar 44100 thenewfile.mpeg

Step 2, now convert the MPEG file to an OGV file :
Open a terminal and type this command line :
ffmpeg2theora thenewfile.mpeg

This produces the desired ogv file, moreover the ogv file is 6MB whilst the original avi was 40MB. I cannot pretend to understand all the parameters used in the above command lines (vauss supplied the correct values) but I hope readers will.

Again thanks to Vauss and all other posters. I am a relative newcomer to Ubuntu and open source but am enjoying the experience and have ditched Windows completely, finding that the best way to learn and discover that there are ways to do everything in open source. I am also still getting used to the forum, its uses and etiquette but like with Ubuntu, hopefully getting better all the time.

By the way, the converted video is now on my website as an ogv file at [http://www.randj.me.uk/photo_galleries/rwanda_10/mov_jali_football.php](http://www.randj.me.uk/photo_galleries/rwanda_10/mov_jali_football.php) - I suspect it only works in Firefox but I have not been able to test it in IE yet (truth be told I am not very interested if it does or not, am I allowed to say that). The video is of a recent visit to Rwanda. When out visiting local communities, we chanced upon local children playing football, the ball being rags and cloths tied up into a round bundle. 

Robin B

---

### Post by Rytron on 2010-10-18
Thank you Robin B.

---

