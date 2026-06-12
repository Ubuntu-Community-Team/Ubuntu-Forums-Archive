---
title: "Help! I can't get sound! I just need to know command"
date: 2006-06-13
forum: Multimedia &amp; Video
---

### Post by rcatman on 2006-06-13
Hey, I seriously need someones help on this. I have a Dell Inspiron 3200 D266XT. I am running ubuntu 5.10 btw. I have found lots of help docs and forum posts addressing the issue of sound particular to this model.

I have found that I need to load the CS4232  driver for sound. In my bios I have audio enabled and the settings are SB=220 WSS=530 AdLib=388 irq=5 dma1=1 dma2=0 .

This post is by someone installing RedHat   [http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg10917.html](http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg10917.html)
another one i found was
[http://damnsmalllinux.org/wiki/index.php/Inspiron_3200_Walkthrough](http://damnsmalllinux.org/wiki/index.php/Inspiron_3200_Walkthrough)

i know d-s-l is debian based so i was hoping they'd be similar. 

I keep running into the fact that I need to have alsa, I've found that its loading the cs4232 mod out of /lib/..$(uname -r)/kernel/drivers/oss  folder and someone recommended i disable oss in the kernel and enable alsa. 

Pretty much I'm lost. I know I'm on the right track but I'm going wrong somewhere. Can anyone PLEASE help? I've managed to get wireless working, customize my window managers and I'm loving Ubuntu! ( did i mention i'm running xubuntu?).  I'd love to get some sound working.

---

