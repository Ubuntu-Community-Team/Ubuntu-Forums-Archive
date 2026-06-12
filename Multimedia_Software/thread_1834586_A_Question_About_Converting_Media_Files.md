---
title: "A Question About Converting Media Files"
date: 2011-08-27
forum: Multimedia Software
---

### Post by dniMretsaM on 2011-08-27
I download my music from Amazon and, as you probably know, it comes in the MP3 format. What I am wondering is do I need an MP3 codec (i.e. LAME or FFmpeg or whatever) to convert those media files to something else (I use Ogg Vorbis)? Because I don't ever play an MP3 file, so I want to remove those codecs if I can (for space and philosophy reasons). If you know the answer, please enlighten me.

---

### Post by BicyclerBoy on 2011-08-27
Amazon does not sell mp3 digital music to non-US residents..

Most (if not all) of the music players will transcode/convert the audio codec formats.
You may need to install the non-free mp3 decoder component for your music player.
This will be a gstreamer or libav* component from medibuntu.

All transcoding/converting reduces quality & introduces artifacts.
You better just to leave them as the are..

I understand your view on mp3, but the owner of mp3 (Frauhofer) has allowed private use at no cost/licence.

The real problem with mp3 is that it was developed for high compression for radio communication links & never for audiophile music.
Often the mp3 offered for sale are too low data rate.

You should complain to: Ubuntu music store for not using flac or ogg, Amazon for using mp3. Then take your business to iTunes (AAC is superior to mp3 but software decode is licensed from mpeg-la).

Amazon need to be abused for not supporting ePUB format eBooks & not supporting ADE DRM..

---

### Post by ron999 on 2011-08-27
Hi
To convert the mp3 to vorbis it needs to de-code the mp3 then en-code the vorbis.
So you need an mp3 _decoder_ of some sort.

---

### Post by dniMretsaM on 2011-08-27
> **BicyclerBoy said:**
> Amazon does not sell mp3 digital music to non-US residents..

So? I don't see what this has to do with anything.

> **BicyclerBoy said:**
> Most (if not all) of the music players will transcode/convert the audio codec formats.
You may need to install the non-free mp3 decoder component for your music player.
This will be a gstreamer or libav* component from medibuntu.

I'm just asking if I need an audio codec to convert my music, not to put it on a media player.

> **BicyclerBoy said:**
> All transcoding/converting reduces quality & introduces artifacts.
You better just to leave them as the are..

I find the Ogg file to be the same or better quality as the MP3. And the compression is better.

> **BicyclerBoy said:**
> I understand your view on mp3, but the owner of mp3 (Frauhofer) has allowed private use at no cost/licence.

I don't care, it is still patent encumbered. And the file sizes are bigger.

> **BicyclerBoy said:**
> The real problem with mp3 is that it was developed for high compression for radio communication links & never for audiophile music.
Often the mp3 offered for sale are too low data rate.

Again, nothing to do with my question,really.

> **BicyclerBoy said:**
> You should complain to: Ubuntu music store for not using flac or ogg, Amazon for using mp3. Then take your business to iTunes (AAC is superior to mp3 but software decode is licensed from mpeg-la).

I'm not complaining, I'm just asking a question. And about iTunes, no. Just no.

> **BicyclerBoy said:**
> Amazon need to be abused for not supporting ePUB format eBooks & not supporting ADE DRM..

(1) I'm fairly active in the campaign for Kindles to support non-DRM'ed ebooks. (2) Nothing should support DRM. DRM is horrible, but that's an entirely different story.

> **ron999 said:**
> Hi
To convert the mp3 to vorbis it needs to de-code the mp3 then en-code the vorbis.
So you need an mp3 _decoder_ of some sort.

Ok, thank you very much! Exactly what I needed to know.

---

### Post by coffeecat on 2011-08-27
> **BicyclerBoy said:**
> Amazon does not sell mp3 digital music to non-US residents..

Then kindly explain how I am able to purchase and download mp3s from Amazon? From the amazon.co.uk site. In Britain. Using Banshee in 11.04, no less. :wink:

---

### Post by BicyclerBoy on 2011-08-27
I never referred to amazon.uk site..
From real experience.
Amazon.com does not sell digital music or games (or some DVD-audio) outside the US.
From your experience..
Amazon UK sells digital music to UK residents..Wow I would have never guessed.

I thought it was might be relevant because of the possible low data rate.
mp3 excels in low data rate not sound quality.

I said music player not media player. I meant PC app like RhythymBox etc.

If you buy mp3 then you support the patent encumbered format.
Can't have it both ways..

Are you serious that you did know you had to decode the mp3 & re-encode to ogg..

Thank you for supporting non-DRM eBooks on Kindle.

---

### Post by dniMretsaM on 2011-08-27
> **BicyclerBoy said:**
> If you buy mp3 then you support the patent encumbered format.
Can't have it both ways..

Are you serious that you did know you had to decode the mp3 & re-encode to ogg.

If there is a site that sells music in a free format, please let me know. I would be very grateful. And it's better than supporting Apple, one of the major DRM pushers. And no, I did not know that. I thought it, but I wanted to ask to make sure.

---

### Post by BicyclerBoy on 2011-08-28
Sorry I only know of:
Linn Records.  (FLAC MP3)
[http://bandcamp.com/](http://bandcamp.com/)   (FLAC OGG etc)
The offerings may not be to your taste.

I would like to find some more free-format music retailers as well.

You can get free music from Jamendo in ogg format but you must use torrent (completely legal).
It is a great shame that the Ubuntu music store is not supporting FLAC or OGG. That could change.

More stuff not related to your question...please ignore.
Modern portable music players are not limited by storage capacity only battery life.
FLAC & ogg are more computational efficient than mp3 so longer battery life & better sound.

---

### Post by mbott on 2011-08-28
Wouldn't SoundConverter have handled this?

-- 
Mike

---

### Post by Eolinwen on 2011-08-28
Hi,
XCFA can do that easily and more.
Try it and you adopt it.

---

