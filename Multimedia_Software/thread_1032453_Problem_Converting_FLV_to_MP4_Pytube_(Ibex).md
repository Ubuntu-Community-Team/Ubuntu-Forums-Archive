---
title: "Problem Converting FLV to MP4 Pytube (Ibex)"
date: 2009-01-06
forum: Multimedia Software
---

### Post by IceQueen on 2009-01-06
I remember when i installed 7.10 I had trouble converting flash videos to mp4 (ipod video), I had to go in synaptic and get some missing codecs, i think i was missing the AAC codecs,

I Upgraded to Ibex yesterday and alas i have the same problem. everytime i try to convert in pytube it simply says "Done" but i have nothing. I've downloaded every codec i can think of (everything pertaining to AAC, ffmpeg, transcode, etc..) and still nothing.

Can anyone tell me what i could possibly be missing? or is there a way to run pytube in debug so i could know where it's going wrong?

Thanks :-)

---

### Post by wolfen69 on 2009-01-06
the best app in the world for ipods and psp's (imo) is [Handbrake]("http://handbrake.fr/rotation.php?file=HandBrake-0.9.3-Ubuntu_GUI_i386.deb"). 1 click to convert almost anything to mp4. could not be any easier. just click the .deb file to install. [Here]("http://handbrake.fr/?article=details") are some details.

---

### Post by ubuntu-freak on 2009-01-06
Have you tried my [howto](http://ubuntuforums.org/showthread.php?t=766683)? There are instructions for installing WinFF, a great GUI front-end for FFmpeg.
 
Also, did you add the Medibuntu repository before you installed FFmpeg, codecs, etc?

---

### Post by pedja_portugalac on 2009-01-06
> **wolfen69 said:**
> the best app in the world for ipods and psp's (imo) is [Handbrake]("http://handbrake.fr/rotation.php?file=HandBrake-0.9.3-Ubuntu_GUI_i386.deb"). 1 click to convert almost anything to mp4. could not be any easier. just click the .deb file to install. [Here]("http://handbrake.fr/?article=details") are some details.

md5sum for handbrake is different from the one on web site and it's case for .deb and for source code as well! Also, I don't like the way they speak to us in README and configure files, makes me feel they are making fun with us. 

avidemux is great tool for reencoding whatever you need and there is an easy Auto format chooser:

[img]http://img155.imageshack.us/img155/2806/screenshotavidemuxax9.jpg[/img]

---

### Post by IceQueen on 2009-01-06
i added the medibuntu repo and i tried updating ffmpeg but that didn't help, something about the version numbers.

I installed HandBrake and it works, the sound quality of the mp4s it produces is much better then that of pytube (no echoey noise).

---

### Post by ubuntu-freak on 2009-01-06
> **IceQueen said:**
> i added the medibuntu repo and i tried updating ffmpeg but that didn't help, something about the version numbers.

 
Try completely removing/purging FFmpeg and install the Medibuntu version.

---

### Post by wolfen69 on 2009-01-06
> **pedja_portugalac said:**
> Also, I don't like the way they speak to us in README and configure files, makes me feel they are making fun with us. 



:rolleyes:

---

### Post by FakeOutdoorsman on 2009-01-06
> **ubuntu-freak said:**
> Try completely removing/purging FFmpeg and install the Medibuntu version.

Medibuntu does not provide ffmpeg for Intrepid.  You can enable some restricted formats in ffmpeg by installing **libavcodec-unstripped-51**.

---

### Post by ubuntu-freak on 2009-01-06
> **FakeOutdoorsman said:**
> Medibuntu does not provide ffmpeg for Intrepid.  You can enable some restricted formats in ffmpeg by installing **libavcodec-unstripped-51**.

Huh? I have it installed and I'm running Intrepid.

Also, my howto installs libavcodec-unstripped-51.

Edit: Hmm... seems you're right. FFmpeg is only in main. Strange.

---

### Post by luwen on 2009-01-07
Yes, [Handbrake is very nice for converting videos and ripping DVD]("http://www.moviesmac.com/tutorial/how-to-use-handbrake-convert-videos-on-mac.html#119").

Also, [iSquint]("http://www.moviesmac.com/news/free-mac-video-converter-discontinued.html#119") is also deserved to try.

---

### Post by andrew.46 on 2009-01-07
Hi IceQueen,

> **IceQueen said:**
> I remember when i installed 7.10 I had trouble converting flash videos to mp4 (ipod video), I had to go in synaptic and get some missing codecs, i think i was missing the AAC codecs,

Can I recommend yet another approach, just to muddy the waters even further? There is an excellent guide on these forums which shows how to install the very latest ffmpeg:

HOWTO: Compile the latest ffmpeg and x264 from source
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

Once this is happily installed the ffmpeg faqs speak specifically on how to convert to format suitable for ipod:

3.12 How do I encode videos which play on the iPod?
[http://ffmpeg.mplayerhq.hu/faq.html#SEC24](http://ffmpeg.mplayerhq.hu/faq.html#SEC24)

Probably a little adjustment required to the settings as the typical flv is pretty low quality. But worth a shot?

All the best,

Andrew

---

