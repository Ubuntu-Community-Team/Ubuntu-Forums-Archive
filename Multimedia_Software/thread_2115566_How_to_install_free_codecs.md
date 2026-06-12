---
title: "How to install free codecs?"
date: 2013-02-13
forum: Multimedia Software
---

### Post by ubunet on 2013-02-13
Hi guys,

My Ubuntu 12.10 x86 can't play some mp4 files. But, I not want to install ubuntu-restricted-extras, only open-source codecs. I wonder which of this **multimedia** codecs it's open-source:

```
sudo apt-get install libdvdcss2 faac faad ffmpeg ffmpeg2theora flac icedax  id3v2 lame libflac++6 libjpeg-progs libmpeg3-1 mencoder mjpegtools  mp3gain mpeg2dec mpeg3-utils mpegdemux mpg123 mpg321 regionset sox  uudeview vorbis-tools x264 arj lha sharutils uudeview mpack cabextract
```

---

### Post by speartip on 2013-02-13
Not sure it's what you want, but try installing VLC, that should play .mp4 files.
 As for what is open source & what is restricted, you best google that one.
I can tell you that libdvdcss2 is open source though.

---

### Post by Bölvaður on 2013-02-13
By the look of the names of the packages you posted, a lot of them aren't codecs at all, but are open-source.

A quick glance over the names of the packages and I would have to guess they are all open source.

Did I guess correctly?
Did I win a prize?

What is the reason why you would want it open source? I can see scenarios where it matters, but the most common scenario is about the licence of the codec it self, not the licence of the software that reads the codec.


ubuntu-restricted-extras contains software of many different licences. But the main reason it is called restricted has probably something to do with how legal it is in some countries to distribute it to. Many codecs are proprietary, like like the mp4 file you were trying to play. But still the programs that encode/decode those formats can be open-source. That means that you can be using open source program to decode a video format that requires you to buy a licence.

So if you (your hardware vendor or your operating system provider) have bought a licence to decode.. lets say h264 videos, then they don't care if you are using open source tools to watch it or not. They are just allowing you to do view it.

It's the codec that is the problem, not the tool you use, unless if you are wanting to view the source code of that tool.

---

### Post by philinux on 2013-02-13
+1 Post #3


See this too. [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by ubunet on 2013-02-13
> **Bölvaður said:**
> By the look of the names of the packages you posted, a lot of them aren't codecs at all, but are open-source.

A quick glance over the names of the packages and I would have to guess they are all open source.

Did I guess correctly?
Did I win a prize?

What is the reason why you would want it open source? I can see scenarios where it matters, but the most common scenario is about the licence of the codec it self, not the licence of the software that reads the codec.


ubuntu-restricted-extras contains software of many different licences. But the main reason it is called restricted has probably something to do with how legal it is in some countries to distribute it to. Many codecs are proprietary, like like the mp4 file you were trying to play. But still the programs that encode/decode those formats can be open-source. That means that you can be using open source program to decode a video format that requires you to buy a licence.

So if you (your hardware vendor or your operating system provider) have bought a licence to decode.. lets say h264 videos, then they don't care if you are using open source tools to watch it or not. They are just allowing you to do view it.

It's the codec that is the problem, not the tool you use, unless if you are wanting to view the source code of that tool.

> **philinux said:**
> +1 Post #3


See this too. [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Ok. Thank you for the explanation!

---

### Post by Bölvaður on 2013-02-13
> **ubunet said:**
> Ok. Thank you for the explanation!
No problem.

Additionally, if you think you will run into legal problems because of those formats you should not install ubuntu-restricted-extras, otherwise there is no reason not to.

Format owners haven't been hunting down individuals (in my country), as far as I know.

---

