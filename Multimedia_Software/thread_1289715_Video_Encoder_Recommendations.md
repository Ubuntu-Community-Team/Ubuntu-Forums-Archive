---
title: "Video Encoder Recommendations"
date: 2009-10-12
forum: Multimedia Software
---

### Post by KoffeeKup on 2009-10-12
Hey guys,

I just re-installed Ubuntu and I was wondering if you guys could recommend any video encoder/converter program that I could use. On Windows, I used XviD4PSP but for some reason, it is not working the way it is supposed to. For the most part, I would want an encoder that could encode .AVI's, .MKVs, and .MP4s to iPod, iPhone, and PSP format.

Also, if you guys know of a way to get XviD4PSP working via Wine, it would be appreciated.

Thanks for the help.

---

### Post by vinutux on 2009-10-13
use handbrake **[http://handbrake.fr/downloads.php]("http://handbrake.fr/downloads.php")**

---

### Post by jeremyswalker on 2009-10-13
> **vinutux said:**
> use handbrake **[http://handbrake.fr/downloads.php]("http://handbrake.fr/downloads.php")**

+1

Excellent program.

---

### Post by KoffeeKup on 2009-10-14
Thanks for the suggestion you too.
However, I need  some sort of option that will allow me to add .srt or .*** subtitles files to the files and encode them together.

---

### Post by RichardLinx on 2009-10-14
Try WinFF. It can encode to iPod, PSP, AVI as well as a few other formats. [http://winff.org/html_new/](http://winff.org/html_new/)
```
sudo apt-get install winff
```
Since you've only just installed you'll probably need a bunch of multimedia codecs. (They don't come installed on Ubuntu by default for legal reasons)
```
sudo apt-get install ubuntu-restricted-extras
```
Enable Medibuntu repositories: ([https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu))
```
sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \
 --output-document=/etc/apt/sources.list.d/medibuntu.list &&
sudo apt-get -q update &&
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get -q update
```
DVD codec:
```
sudo apt-get install libdvdcss2
```
w32 codecs:
```
sudo apt-get install w32codecs
```

For .MKV you'll need Avidemux: [http://fixounet.free.fr/avidemux/](http://fixounet.free.fr/avidemux/)
```
sudo apt-get install avidemux
```

I don't know about converting video to an iPhone readable format though. But for the rest you should be fine with most of what I just mentioned installed. :)

Edit: Just in case you don't know (Just realized you only have two posts, brand new to Linux?) you need to paste all those commands into a terminal. Terminal can be opened via Applications > Accessories > Terminal

---

### Post by KoffeeKup on 2009-10-17
So I've installed everything and tried converting with Avidemux. A video file for the PSP. I selected the Video to be MPEG4-AVC, Audio to Copy and Format to MP4 (PSP). The encode went fine. However, when I transferred it to my PSP, it came up as "Unsupported Data". I looked over the Info file and the audio was recognized but the video wasn't. Anything I could do to fix this?

I also won't use WinFF much since that gave me an encode that worked but in a really bad quality.

---

