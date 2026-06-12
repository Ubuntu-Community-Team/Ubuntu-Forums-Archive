---
title: "I can't play videos"
date: 2009-04-06
forum: Multimedia Software
---

### Post by LUIWOMBAT on 2009-04-06
for some reason I can't play videos mp4 or anything else on xines,vlc or totem.The same thing goes for the music player amarock and others. Some times i get part of the screen blue,other times it simply doesn't recognize it.,for this reason I'M always force to go back to windows and use windows media player which is very stable.For me having linux with no stable media or music player is like having a body and chassis in a car but not engine.I HAVE A ACER 5610 WITH INTEL PENTIUM DUAL CORE 2GB MEM AND ABOUT 40 GB HD SPACE FOR UBUNTU 8.04:guitar:

---

### Post by UbuntuNerd on 2009-04-06
follow this quick [guide](http://my.opera.com/ubuntunerd1/blog/how-to-play-quicktime-videos-and-other-media-with-totem)

---

### Post by Bölvaður on 2009-04-06
let me try one thing out : [apt://ubuntu-restricted-extras](apt://ubuntu-restricted-extras)
^^ it works :P install, the ubuntu-restricted-extras, which gets most of the codecs needed.

if that doesnt work open the terminal (applications &#8594; accessories &#8594; terminal) and enter this:

```
lspci
```

now look for your video card and post it here.
[]("http://ubuntuforums.org/apt//ubuntu-restricted-extras")

---

