---
title: "cant make sound work in feisty"
date: 2007-05-19
forum: Multimedia &amp; Video
---

### Post by karaju on 2007-05-19
hello,
I have installed feisty recently dual booting with Winxp. I am new to linux. My sound is not working at all in feisty while it is working fine in winxp. I have sound card Via8237 in motherboard and an additional card YMF724 (Yamaha), which is configured for winxp and is working fine.

I have followed different methods suggested different fora including Ubuntu and I could not make sound work. Then I came across this site [http://alsa-project.org/alsa-doc/doc-php/template.php?company=Yamaha&card=&chip=YMF724&module=ymfpci](http://alsa-project.org/alsa-doc/doc-php/template.php?company=Yamaha&card=&chip=YMF724&module=ymfpci) [^] and following the instructions, I have got the following out put:

raju@raju-desktop:~$ modinfo soundcore
filename: /lib/modules/2.6.20-15-generic/kernel/sound/soundcore.ko
alias: char-major-14-*
license: GPL
author: Alan Cox
description: Core sound module
srcversion: 45750F13477CBA5B6F36F46
depends:
vermagic: 2.6.20-15-generic SMP mod_unload 586
raju@raju-desktop:~$ cd /usr/src
raju@raju-desktop:/usr/src$ mkdir alsa
mkdir: cannot create directory `alsa': Permission denied
raju@raju-desktop:/usr/src$

Now please tell me what to do further..........

Thanks in advance.
 karaju

---

### Post by Dekunuts on 2007-05-19
maybe your sound is muted. If you type alsamixer in a terminal, you can change volume settings or even by double clicking on the sound icon at the top right (if you haven't (re)moved it)

---

### Post by karaju on 2007-05-19
hello,
i am unable to install drivers for sound cards so far.............that i have already explained
thanks

---

