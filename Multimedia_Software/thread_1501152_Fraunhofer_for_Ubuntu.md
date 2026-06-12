---
title: "Fraunhofer for Ubuntu?"
date: 2010-06-03
forum: Multimedia Software
---

### Post by Spook50 on 2010-06-03
Quicky here: is there a legit (read: legal) way of getting the Fraunhofer MP3 codec in Ubuntu? Any commercial or freeware compressors that use it, or maybe even a standalone codec installer (like Radium for Windows, though IIRC that one's not exactly legal)?

If not, is there perhaps a better codec for compressing MP3s? I've used Fraunhofer at 256Kbps CBR for years and never had a problem. Always sounded outstanding on my iPod (and really shined when I invested in a good pair of canal phones), but if there's something out there that might be better, I'm wiling to give it a shot.

---

### Post by babarosa on 2010-06-04
Hi,

the open source equivalent to mp3 is ogg, it is also a compression algorithmus _with quality loss_. The results of an ogg-encoding are at least equal or better to mp3.

A free open source _lossless_ codec is FLAC.

Asunder for example is an application which provides cd ripping with ogg and FLAC support. You'll find the latest version here 

Karmic:
[https://launchpad.net/~ferramroberto/+archive/linuxfreedomkarmic](https://launchpad.net/~ferramroberto/+archive/linuxfreedomkarmic)

Lucid:
[https://launchpad.net/~ferramroberto/+archive/linuxfreedomlucid](https://launchpad.net/~ferramroberto/+archive/linuxfreedomlucid)

---

### Post by pickarooney on 2010-06-04
What percentage of hardware music playback devices suport OGG format? I've personally never seen one.

---

### Post by Rhubarb on 2010-06-04
> **pickarooney said:**
> What percentage of hardware music playback devices suport OGG format? I've personally never seen one.

Many ipods can play ogg vorbis / flac with the rockbox firmware:
[http://www.rockbox.org/](http://www.rockbox.org/)

Sandisk make some:
[http://www.sandisk.com/products/sansa-music-and-video-players](http://www.sandisk.com/products/sansa-music-and-video-players)

So do Archos:
[http://www.archos.com/](http://www.archos.com/)

Also iriver:
[http://www.iriver.com](http://www.iriver.com)

And Cowon:
[http://www.cowonglobal.com/](http://www.cowonglobal.com/)

And some Creative players:
[http://au.creative.com/products/feature.asp?category=213&](http://au.creative.com/products/feature.asp?category=213&)

As well as some Philips players:
[http://www.consumer.philips.com/c/mp3-and-mp4-players/25476/cat/au/](http://www.consumer.philips.com/c/mp3-and-mp4-players/25476/cat/au/)

I believe Samsung used to make flash-based music players that supported ogg vorbis and / or flac as well - but Samsung have ceased making music players now.

If you want a legitimate mp3 codec, see here:
[http://shop.canonical.com/index.php?cPath=19](http://shop.canonical.com/index.php?cPath=19)

Otherwise, if you just want mp3 for free, grab **lame** from the repositories:
```
sudo aptitude install lame
```

But really, if you can, just use ogg vorbis for portable mp3 players - it has much better audio quality than mp3, or just use flac if space isn't an issue (flac is lossless audio compression).

---

### Post by Spook50 on 2010-06-04
> **babarosa said:**
> Hi,
 
the open source equivalent to mp3 is ogg, it is also a compression algorithmus _with quality loss_. The results of an ogg-encoding are at least equal or better to mp3.
 
A free open source _lossless_ codec is FLAC.
 
Asunder for example is an application which provides cd ripping with ogg and FLAC support. You'll find the latest version here 
 
Karmic:
[https://launchpad.net/~ferramroberto/+archive/linuxfreedomkarmic](https://launchpad.net/~ferramroberto/+archive/linuxfreedomkarmic)
 
Lucid:
[https://launchpad.net/~ferramroberto/+archive/linuxfreedomlucid](https://launchpad.net/~ferramroberto/+archive/linuxfreedomlucid)
 
 
I've read a bit about FLAC and played a bit with OGG, but each time I end up coming back to MP3. I have an archive of 4000+ MP3s and in addition to the smaller filesize, I can't even hear any faults in the audio on the MP3s I've done. That, plus I'm so used to the ID3 tagging, I'd like to stick with that if possible.

---

### Post by iconoclast hero on 2011-04-18
Can I just take the encoder that I used in Windows that I purchased a license to and simply drop it somewhere to use that?  I read all the arguments about LAME vs. the Fraunhoffer IIS encoder and the advantage of ogg.  I don't know if my creative zen can play ogg or not, but  nothing I have tried can beat Fraunhoffer on the size of **low quality**compression.  When I rip an audio book, I don't care if the sound is crappy, I'm concerned about the size of it.

I do use LAME for music.

---

### Post by Chronon on 2011-04-19
If you're transcoding audio books try the Speex codec instead.

---

### Post by iconoclast hero on 2011-04-19
> **Chronon said:**
> If you're transcoding audio books try the Speex codec instead.

Thanks, I'll give it a whirl, it looks like the vision m supports ogg.  The only problem I have had is that no one else I know knows what an .ogg file is.  Come to think of it they probably don't know what AAC, M4P, M4U are either.  As long as I get the same quality for the same price in size, I'm happy.  I think last time I tried, I encoded with ogg/vorbis and it was not even close.

---

