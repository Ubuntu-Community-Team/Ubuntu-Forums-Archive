---
title: "Converting to OGG"
date: 2008-09-12
forum: Multimedia Software
---

### Post by Jimmey on 2008-09-12
Is there an easy way to convert an entire collection of music from mixed MP3/WMA to OGG?

Thanks.

---

### Post by emu42 on 2008-09-12
[http://www.freemp3wmaconverter.com/](http://www.freemp3wmaconverter.com/)

---

### Post by eye208 on 2008-09-13
> **Jimmey said:**
> Is there an easy way to convert an entire collection of music from mixed MP3/WMA to OGG?
Yes, but you don't want to do that. It's pointless.

---

### Post by emu42 on 2008-09-13
I needed to convert to .ogg because I had a computer that had Ubuntu, but didn't have internet. Thus, I couldn't download plugins to the (non-open source) .mp3 and .wma codecs.

---

### Post by biosater on 2008-09-14
```
sudo apt-get install soundconverter
```

---

### Post by eye208 on 2008-09-14
> **emu42 said:**
> I needed to convert to .ogg because I had a computer that had Ubuntu, but didn't have internet. Thus, I couldn't download plugins to the (non-open source) .mp3 and .wma codecs.
I don't get it. You were able to download "Free Mp3/Wma/Ogg Converter" but not the codecs from [http://packages.ubuntu.com/](http://packages.ubuntu.com/)? That doesn't make sense. What am I missing?

@Jimmey: Converting from MP3/WMA to Ogg Vorbis will result in crappy sound quality because the compression artifacts add up. Please don't do it. Ogg Vorbis is superior to MP3/WMA only when applied to audio that has not been compressed before. Transcoding from one lossy compression scheme to another will _always_ degrade quality.

---

### Post by skullmunky on 2008-09-16
Unless you have two computers with ubuntu, one with internet and one without ... ?

---

### Post by eye208 on 2008-09-16
Downloading the codecs for Ubuntu does not require Ubuntu. If you can transfer the files for conversion or the converter itself, you can transfer the codec packages as well.

---

