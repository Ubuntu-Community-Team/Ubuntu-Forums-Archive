---
title: "Open Sourcing my Music"
date: 2011-12-07
forum: Multimedia Software
---

### Post by teejay17 on 2011-12-07
[COLOR=#000000][FONT=Arial]I  want to “open source” my music collection. Stupid me, back when I first  bought an iPod in ‘04 or ‘05, I let iTunes rip my CDs into AAC, not  knowing the limitations that would pose in the future. [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]So I have a few question regarding this topic:[/FONT][/COLOR]
[LIST=1]
[*][COLOR=#000000][FONT=Arial]Which  codec should I use between FLAC and Ogg Vorbis? I’ve heard good things  about FLAC, but I’m concerned it will take up a lot of space. Also, my  music collection is between 128 and 192 bitrate, so I’m wondering if  FLAC can even make that sound “good.” [/FONT][/COLOR]
[*][COLOR=#000000][FONT=Arial]With respect to Ogg Vorbis, I’ve read that it doesn’t allow meta-data embedding in the files. Is this true?[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Arial]What’s  the best program for the big conversion from AAC (some MP3s) to either  FLAC and/or Ogg Vorbis? (I may be doing some of the conversions on  Windows, so I’m also interested in a good open-source Windows converter)[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Arial]I guess Rockbox is the only way to get FLAC and Ogg Vorbis to play on my iPods? [/FONT][/COLOR]
[*][COLOR=#000000][FONT=Arial]Anything else I should be aware of going into this project? [/FONT][/COLOR]
[/LIST]

[COLOR=#000000][FONT=Arial]Thanks everyone, in advance![/FONT][/COLOR]

---

### Post by teejay17 on 2011-12-07
> **teejay17 said:**
> [COLOR=#000000][FONT=Arial]I  want to “open source” my music collection. Stupid me, back when I first  bought an iPod in ‘04 or ‘05, I let iTunes rip my CDs into AAC, not  knowing the limitations that would pose in the future. [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]So I have a few question regarding this topic:[/FONT][/COLOR]
[LIST=1]
[*][COLOR=#000000][FONT=Arial]Which  codec should I use between FLAC and Ogg Vorbis? I’ve heard good things  about FLAC, but I’m concerned it will take up a lot of space. Also, my  music collection is between 128 and 192 bitrate, so I’m wondering if  FLAC can even make that sound “good.” [/FONT][/COLOR]
[*][COLOR=#000000][FONT=Arial]With respect to Ogg Vorbis, I’ve read that it doesn’t allow meta-data embedding in the files. Is this true?[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Arial]What’s  the best program for the big conversion from AAC (some MP3s) to either  FLAC and/or Ogg Vorbis? (I may be doing some of the conversions on  Windows, so I’m also interested in a good open-source Windows converter)[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Arial]I guess Rockbox is the only way to get FLAC and Ogg Vorbis to play on my iPods? [/FONT][/COLOR]
[*][COLOR=#000000][FONT=Arial]Anything else I should be aware of going into this project? [/FONT][/COLOR]
[/LIST]

[COLOR=#000000][FONT=Arial]Thanks everyone, in advance![/FONT][/COLOR]
Well I'm on my way to answering question 3. I found this so far: [http://www.vorbis.com/setup_windows/](http://www.vorbis.com/setup_windows/)

---

### Post by ron999 on 2011-12-07
> **teejay17 said:**
> I  want to “open source” my music collection.
Why?

---

### Post by m_duck on 2011-12-07
If you are just transcoding your existing (lossy) AAC and MP3 files, don't bother with flac - they will just end up being huge files with no real gain. If you are ripping from the CDs again however, flac would be a good choice if you have the storage space. That said, it does depend a lot on what you are using to listen to your audio.

The issue with transcoding your current files is that they are already lossy (i.e. information lost from the original cd-quality tracks) so if you a) transcode to ogg, you will lose more information, regardless of bitrate chosen (ogg is also lossy), or b) transcode to flac, you will have the same quality as your current files but they will be much larger (since flac is lossless).

I would probably suggest keeping your music as it is, unless there is a specific problem with it - unless of course you have access to the original CDs, in which case I would probably re-rip from them.

---

### Post by teejay17 on 2011-12-07
> **m_duck said:**
> If you are just transcoding your existing (lossy) AAC and MP3 files, don't bother with flac - they will just end up being huge files with no real gain. If you are ripping from the CDs again however, flac would be a good choice if you have the storage space. That said, it does depend a lot on what you are using to listen to your audio.

The issue with transcoding your current files is that they are already lossy (i.e. information lost from the original cd-quality tracks) so if you a) transcode to ogg, you will lose more information, regardless of bitrate chosen (ogg is also lossy), or b) transcode to flac, you will have the same quality as your current files but they will be much larger (since flac is lossless).

I would probably suggest keeping your music as it is, unless there is a specific problem with it - unless of course you have access to the original CDs, in which case I would probably re-rip from them.
Those are excellent points. I've since been experimenting with[ Fre:ac ]("http://www.bonkenc.org/")and I see how this is so. Interestingly though (and perhaps this is imagination) Ogg Vorbis sounds "fuller" at the same bit rate (converted from AAC). 
As for my original CDs, unfortunately, my brother "borrowed" my them after I bought my iPod and they have since disappeared into the ether.

---

### Post by teejay17 on 2011-12-07
> **ron999 said:**
> Why?
Personal choice. I want to have two separate versions (AAC and Flac/Ogg) of my music backed up.

---

