---
title: "mp3 ripper for Ubuntu"
date: 2008-06-23
forum: Multimedia Software
---

### Post by hemajith on 2008-06-23
I'm using Hardy Heron. Can anyone please tell me a good mp3 ripper for Ubuntu? I heard that you could do this with sound juicer too but I don't have it in this installation. If there is ANY good ripping software that I can install, it will be great.

---

### Post by ahbart on 2008-06-23
You should be able to install sound-juicer If you want to try this:
sudo apt-get install sound-juicer

Or you could try grip:
sudo apt-get install grip
With grip you have to check some more settings. But I love this one.
Maybe you will need to install lame or liblame1 also.

---

### Post by Zulu-Zeffir on 2008-06-23
Why don't you just install sound juicer?

aptitude install sound-juicer

---

### Post by CH1C0 on 2008-06-23
Audio CD Extractor. :guitar:

---

### Post by hemajith on 2008-06-23
> **ahbart said:**
> You should be able to install sound-juicer If you want to try this:
sudo apt-get install sound-juicer

Or you could try grip:
sudo apt-get install grip
With grip you have to check some more settings. But I love this one.
Maybe you will need to install lame or liblame1 also.

I installed sound-juicer and I can rip to .ogg. But I can't set the default format to mp3! It shows in the preferences but does not show in the pull down menu of default format. I installed lame too. How do I et around this?

---

### Post by ahbart on 2008-06-23
maybe liblame0 should do the trick than.

---

### Post by hemajith on 2008-06-23
> **ahbart said:**
> maybe liblame0 should do the trick than.

liblame0 is already the newest version, it says!

---

### Post by hemajith on 2008-06-23
I've found a site that helps to install all the codecs. It's

[http://www.stchman.com/cd_rip.html](http://www.stchman.com/cd_rip.html)

And all started working.

Thank you for the help

---

### Post by ahbart on 2008-06-23
One of the first things I install when I do a clean system install is 
install the non-free-codecs package in synaptic. maybe that would have done the trick too.

---

### Post by forger on 2008-06-23
> **hemajith said:**
> I installed sound-juicer and I can rip to .ogg. But I can't set the default format to mp3! It shows in the preferences but does not show in the pull down menu of default format. I installed lame too. How do I et around this?

give this a go:
```
sudo apt-get install lame vorbis-tools flac ffmpeg liblame0 gstreamer0.10-plugins-bad gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly gstreamer0.10-ffmpeg gstreamer0.10-plugins-base gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad-multiverse libdvdread3 gstreamer0.10-x gstreamer0.10-fluendo-mp3
```

---

### Post by ahbart on 2008-06-23
If you have made some changes to the repository list:
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

