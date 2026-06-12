---
title: "Flash Player installation"
date: 2009-05-26
forum: Multimedia Software
---

### Post by Rabbut on 2009-05-26
Hi all,

I'm trying to install Adobe Flash player for Linux onto a handful of computers running Ubuntu Jaunty Jackolope 9.04. The .tar.gz, .rpm and .deb packages all fail to install throwing a error of "your architecture \'X86_64\' isn't supported by Adobe installer". I've tried getting in touch with Adobe, and had a rather un-helpful reply, basically a link to their install instructions and a note saying my case has been closed... despite telling them I'd followed their instructions to the letter in my query :(

So....

Does anyone here have Adobe Flash Player installed on their computers? If so, could you please offer any suggestions/advice of getting round this issue. If Flash won't work, is there an alternative plug-in that I may use to view Flash content?

Thanks a lot to anyone whom replies :D
Rabbut

---

### Post by gandaran on 2009-05-26
install the ubuntu restricted-extras package from synaptic package manager, this package includes codecs, fonts and adobe flash 32-bits, if you find any problem with the 32-bits flash on your 64-bits system remove the flashplugin-nonfree and or flashplugin-installer and nspluginwrapper installed with the ubuntu-restricted-extras package then follow these [instructions]("http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml") for installing 64-bits flash.

---

### Post by stefangr1 on 2009-05-26
You can use the 64-bits version of flashplayer:

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)


Installation instructions are here:
[http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html#install](http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html#install)

---

### Post by Rabbut on 2009-05-27
Thanks a lot for that folks, worked a treat:D

---

### Post by hyperdude111 on 2009-05-27
If you want other codecs ; mp3,avi,mp4,flv etc.... use the code

```
sudo apt-get install ubuntu-restricted-extras
```

---

