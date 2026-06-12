---
title: "Enable all audio and video codecs without X"
date: 2010-07-11
forum: Multimedia Software
---

### Post by nothingspecial on 2010-07-11
How do I install all audio and video codecs without installing X.

I would like to use an old computer to stream, convert, rip........etc my music and video.

When I try to install all the necessary codecs apt wants to pull in X

Can I mess about with every audio and video format with a cli only install?

---

### Post by ajgreeny on 2010-07-11
I maybe wrong, but surely you need x to be able to play any video files.  However try enabling the medibuntu repos with
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
then ```
sudo apt-get update
sudo apt-get install w32codecs
```
which do not appear to have any x packages in the dependencies list.

---

### Post by nothingspecial on 2010-07-11
Thanks.

I would like this old, resource light computer, to crunch away, converting my ripped dvds to mp4 with ffmpeg. As well as stream my flac, ogg, mp3 and occasional m4a collection to my various squeezeboxes.

The music collection appears to work, allthough I can`t possibly know if everything does due to the size of it.

At the moment, I cannot stream radio

I can see why I might need X to have all the video codecs installed, it`s just that I have no interest in playing them on that machine, just using it`s processing power to convert them.

Thankyou for you reply

---

### Post by nothingspecial on 2010-07-11
> **nothingspecial said:**
> Thanks.



I can see why I might need X to have all the video codecs installed, it`s just that I have no interest in playing them on that machine, just using it`s processing power to convert them.



And I would like to stream them to machines who have the capability to play them, if you see what I mean.

---

### Post by nothingspecial on 2010-07-11
> **ajgreeny said:**
> I maybe wrong, but surely you need x to be able to play any video files.  However try enabling the medibuntu repos with
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```then ```
sudo apt-get update
sudo apt-get install w32codecs
```which do not appear to have any x packages in the dependencies list.

There is no w32codecs on my 64bit server. apt-cache references non-free-codecs which also wants to install X

Maybe this is not possible

---

### Post by nothingspecial on 2010-07-11
w64codecs obviously :-\"

---

### Post by nothingspecial on 2010-07-11
Close but no cigar.

You know, it works as far as I can tell, so far, if I install everything and don`t startx.

So I`m happy

ish

---

