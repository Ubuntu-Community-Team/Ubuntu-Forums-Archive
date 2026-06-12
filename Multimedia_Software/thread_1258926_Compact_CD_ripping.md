---
title: "Compact CD ripping"
date: 2009-09-05
forum: Multimedia Software
---

### Post by jayleesan on 2009-09-05
I am not sure about this.
I have a 40 GB media PC installed for playing audio only.
What format for ripping CD's is the most compact way? So I can have as much music as poussible on it?
Thanks!

---

### Post by jordilin on 2009-09-05
Ogg format is the recommended one ;). If you want this music to be stored in portable players then maybe mp3.

---

### Post by jayleesan on 2009-09-05
> **jordilin said:**
> Ogg format is the recommended one ;).
How many audio CD's can be stored in OGG format on 30 GB you think?
Is the bitrate ajustable in Rhythmbox?
Still got to figure this out...

---

### Post by andrew.46 on 2009-09-05
Hi jayleesan,

> **jayleesan said:**
> What format for ripping CD's is the most compact way? So I can have as much music as poussible on it?

You may need to experiment with the device itself and see what sounds best. Most people would be happy with a bitrate of 128k and this would yield the best size / quality ratio for your purposes I suspect. As for format ogg vorbis *should* be your friend as it is open source and has great sound quality relative to file size but the world seems to be running with mp3 these days...

Andrew

---

### Post by jayleesan on 2009-09-05
> **andrew.46 said:**
> Hi jayleesan,



You may need to experiment with the device itself and see what sounds best. Most people would be happy with a bitrate of 128k and this would yield the best size / quality ratio for your purposes I suspect. As for format ogg vorbis *should* be your friend as it is open source and has great sound quality relative to file size but the world seems to be running with mp3 these days...

Andrew

Thanks for that! This thing is not to connect to the world ;)
I am using a old desktop PC te set up a juke-box to be used at the office. It's to replace a CD-changer which holds up to 200 CD's.

I wonder if I can find a format to stack all this audio on the 40GB drive (next to ubuntu dapper).

Lets say I go for 96k. Would ogg or mp3 be the better choice?

---

### Post by tgalati4 on 2009-09-06
I personally like mp3 in 192 kbps VBR.  You need to test some music that you normally listen to and rip to 96, 128, and 192 CBR and see if you can tell the difference on your system.  If you can then try 128 VBR or 192 VBR and see if there is an improvement.  I like OGG as well, but not many portable players support it.  If the music will only be played on the PC then OGG is perhaps more efficient.

Again try OGG at 96 and MP3 at 96 and see if you can tell the difference.  Then compare the file sizes.

One test is worth a thousand expert opinions.

Most of the music breakdown occurs at high frequencies 15K to 20K Hz.  Cymbals, crash, and other percussion will get "gainy" and less defined at 96.  If your system can't reproduce those frequencies, or if you can't hear them clearly, then you can save space using 96 or 128 versus 192 bitrates.

A google search will yield some interesting, detailed studies of this with charts and impressions.

---

### Post by jayleesan on 2009-09-06
Thanks for replying! I'll do my searching...

---

### Post by scragar on 2009-09-06
> **tgalati4 said:**
> I personally like mp3 in 192 kbps VBR.  You need to test some music that you normally listen to and rip to 96, 128, and 192 CBR and see if you can tell the difference on your system.  If you can then try 128 VBR or 192 VBR and see if there is an improvement.  I like OGG as well, but not many portable players support it.  If the music will only be played on the PC then OGG is perhaps more efficient.

Again try OGG at 96 and MP3 at 96 and see if you can tell the difference.  Then compare the file sizes.

One test is worth a thousand expert opinions.

Most of the music breakdown occurs at high frequencies 15K to 20K Hz.  Cymbals, crash, and other percussion will get "gainy" and less defined at 96.  If your system can't reproduce those frequencies, or if you can't hear them clearly, then you can save space using 96 or 128 versus 192 bitrates.

A google search will yield some interesting, detailed studies of this with charts and impressions.
Ogg doesn't have bitrates like MP3 does, it has quality levels, from, I think, 4 to 10(could be wrong), I believe a 6 or 7 is around 196 on the MP3 scale, but I could be wrong.
Either way ogg will be smaller for the quality, the question is how much quality do you really need?

---

### Post by jocheem67 on 2009-09-06
I like ogg, being it open-source and patent free...
It gets more credit on the audio techy websites too. Further more it's native on ubuntu installs through libvorbis.

I wouldn't go under -q 5 or 6 though as it'll gain more songs but yo, my ears wouldn't like it at all....:D

Never do a re-encode, as it's not a good idea to compress from an already lossy format. No need to go from a 128k mp3 to let's say a -q 5 ogg...

---

### Post by Bucky Ball on 2009-09-06
I have a Cowon iAudio 7 which holds over 500 FLAC music files on 8Gb. Ogg Vorbis is unusual an portable players, FLAC even rarer so MP3 might be your only option anyway. Better check what your device is capable off before looking too much further. That may dictate what you do.

---

### Post by 3rdalbum on 2009-09-06
Maybe try AAC, it generally sounds reasonable at 96 kilobits per second, but I'm not sure how good the Linux encoders for it are.

---

### Post by andrew.46 on 2009-09-06
Hi 3rdalbum,

> **3rdalbum said:**
> Maybe try AAC, it generally sounds reasonable at 96 kilobits per second, but I'm not sure how good the Linux encoders for it are.

It has been a while for me but the Nero AAC encoder seemed to do a pretty reasonable job, certainly producing superior sound to my uneducated ears than faac. I don't know of any linux guis that utilise this though, it would be a case of ripping with something like cdparanoia and then transcoding with neroAacEnc by hand or script. This might not be what the OP is after I suspect for a great number of cds...

Andrew

---

