---
title: "Decrypting Video files?"
date: 2011-10-09
forum: Multimedia Software
---

### Post by SamHack on 2011-10-09
Hi all. I've recently switched to Ubuntu 11.04 after windows failed on me for the last time.

So far I've been very impressed although I'm the first to admit i'm not the most hardcore pc user. I am however having a problem with encrypted video files. I've managed to get the dvd's to run properly but I have several films that let you transfer a digital copy straight from the disk. Its mainly the Family Guy starwars trilogy but there are others to. I have all the original codes for them but they are still encrypted so I can't view them on vlc.

Is there anyway to solve this.

Many thanks

Sam

---

### Post by Dangertux on 2011-10-09
We don't support circumventing Digital Rights Management.

---

### Post by shantiq on 2011-10-09
> **SamHack said:**
> Hi all. I've recently switched to Ubuntu 11.04 after windows failed on me for the last time.

So far I've been very impressed although I'm the first to admit i'm not the most hardcore pc user. I am however having a problem with encrypted video files. I've managed to get the dvd's to run properly but I have several films that let you transfer a digital copy straight from the disk. Its mainly the Family Guy starwars trilogy but there are others to. I have all the original codes for them but they are still encrypted so I can't view them on vlc.

Is there anyway to solve this.

Many thanks

Sam


[URL="https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs"][B]===>there sam
[/B][/URL]    at least this  ```
sudo apt-get install  libdvdcss2

```   in your terminal

---

### Post by SamHack on 2011-10-09
> **Dangertux said:**
> We don't support circumventing Digital Rights Management.

I'm sorry but I didn't mean for it to come across like that. I purchased the original media that supports a transfer of a digital copy that can be used to play the media disk free on your pc or any portable device. It just seems that the file transfer system isn't compatible with linux systems. I was simply trying to find a way to make this work.

---

### Post by 4Orbs on 2011-10-09
I've used the free digital copy available on some discs, but couldn't get it to work on linux. It seems to work only with Windows or Mac. In my case it needed the Windows Media Center/Windows Media Player to function properly.

---

### Post by Dangertux on 2011-10-09
> **SamHack said:**
> I'm sorry but I didn't mean for it to come across like that. I purchased the original media that supports a transfer of a digital copy that can be used to play the media disk free on your pc or any portable device. It just seems that the file transfer system isn't compatible with linux systems. I was simply trying to find a way to make this work.



No worries I am pretty sure I misread your original post. My fault. Glad it worked.

---

### Post by SamHack on 2011-10-09
> **Dangertux said:**
> No worries I am pretty sure I misread your original post. My fault. Glad it worked.

Ah it hasn't worked. Think I should have worded that last sentence with a little more care.

---

### Post by Dangertux on 2011-10-09
> **SamHack said:**
> Ah it hasn't worked. Think I should have worded that last sentence with a little more care.


Ahh - well , from the brief research I did (video decryption isn't my thing) ; it appears to be an itunes format rip of the dvd. 

Which brings us right back around to DRM circumvention. I can't help you with that as I stated above because itunes formatted files do have DRM, which are not supported by Ubuntu. The only advice I can give you is to look into handbrake.

Good luck.

---

### Post by BUCH on 2011-10-11
You could try encoding the digital copies to another format.  The best and quickest encoder I've found is an [FLV converter]("http://www.flv.com/flvconverter.html")

---

### Post by mikewhatever on 2011-10-11
> **BUCH said:**
> You could try encoding the digital copies to another format.  The best and quickest encoder I've found is an [FLV converter]("http://www.flv.com/flvconverter.html")

But DVDs don't use flv..., besides, that's a Windows only program.

---

### Post by Frogs Hair on 2011-10-11
Look into adding this repository if you haven't already . There are some codecs that may help . [http://www.unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1656-how-to-add-medibuntu-repository-in-ubuntu-via-terminal-and-gui](http://www.unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1656-how-to-add-medibuntu-repository-in-ubuntu-via-terminal-and-gui)

---

