---
title: "Resize Xvid to DivX and merge subtitle."
date: 2008-01-29
forum: Multimedia &amp; Video
---

### Post by BMOE on 2008-01-29
Hello.

I've just bought a new mobile phone (LG KU990 "Viewty") and I would like to watch videos on it. It supports DivX but not Xvid, and subtitles are not supported.

I have some videos in Xvid format with a srt subtitle.

What I want to do is merge the subtitle to the Xvid, then resize the Xvid to 480*270 and to get it i DivX format.

It seems that the phone can play Xvid's if the header of the file is changed to a DivX header.

How do I do this conversion? What tools do I need? Is there any guide out there?

Thanks.
/Matias

---

### Post by eye208 on 2008-01-29
> **BMOE said:**
> I have some videos in Xvid format with a srt subtitle.

What I want to do is merge the subtitle to the Xvid, then resize the Xvid to 480*270 and to get it i DivX format.
You can do that with Avidemux (sudo apt-get install avidemux).

> It seems that the phone can play Xvid's if the header of the file is changed to a DivX header.
It depends on how the Xvid encoder was configured. Some of Xvid's advanced features are not supported by DivX and may therefore not work on the target device, even if you fake the file to be DivX. A guide on which features have to be disabled for DivX compatibility can be found [here](http://www.animemusicvideos.org/guides/avtech/xvid.html).

Faking a DivX AVI file is quite simple: You can use the tool cfourcc (sudo apt-get install cfourcc) to change the four-character code of the video stream from XVID to DX50. Avidemux also includes this function. If I remember correctly, it even chooses the DX50 tag by default.

---

