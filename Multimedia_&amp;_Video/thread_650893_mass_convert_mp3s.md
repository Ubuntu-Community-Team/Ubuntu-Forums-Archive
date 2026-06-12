---
title: "mass convert mp3s"
date: 2007-12-26
forum: Multimedia &amp; Video
---

### Post by rkakkar on 2007-12-26
I am looking to mass convert the bitrates for a large number of mp3s. I accidentally ripped them at 320 kbps. I would like to convert them to 192 kbps. I have looked at audio-convert but it doesn't do what I need. I know lame would be the way to go but I know nothing about bash scripts. I want to create a loop that will convert everything in a given directory and all sub-folders beneath that.

Any ideas?

---

### Post by schaumkeks on 2007-12-27
> **rkakkar said:**
> I am looking to mass convert the bitrates for a large number of mp3s. I accidentally ripped them at 320 kbps. I would like to convert them to 192 kbps. I have looked at audio-convert but it doesn't do what I need. I know lame would be the way to go but I know nothing about bash scripts. I want to create a loop that will convert everything in a given directory and all sub-folders beneath that.

Any ideas?

First of all, I do not recommend reconverting those files because it will result in more loss of quality than if you would convert them to the lower bitrate from the original source.

If you really don't have the original source anymore you could try the GUI soundconverter.
```
sudo apt-get install soundconverter
```
There you can easily add all relevant files, change the preferences to output to MP3 VBR High Quality and another output directory (IMPORTANT! or you will overwrite the source MP3 files).

Bye, Sven

---

