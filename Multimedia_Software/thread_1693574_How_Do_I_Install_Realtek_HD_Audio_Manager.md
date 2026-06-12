---
title: "How Do I Install Realtek HD Audio Manager?"
date: 2011-02-23
forum: Multimedia Software
---

### Post by LonelyAspie on 2011-02-23
I downloaded the file from Realtek's website. It says it's for Linux/Unix so I assume it's also compatible to Ubuntu.

I attempted to install and even made a video about it here:
[http://www.youtube.com/watch?v=p85ouyuHaD8](http://www.youtube.com/watch?v=p85ouyuHaD8)

I tried again with the from the root terminal (sudo su root command) but no luck. I emailed 
Realtek and thiss is what they said:

"
[FONT=&#26032;&#32048;&#26126;&#39636;]1. open a "termainal"[/FONT]
 [FONT=&#26032;&#32048;&#26126;&#39636;]2. "sudo su root"  enter the root  password [/FONT]
 [FONT=&#26032;&#32048;&#26126;&#39636;]3.  copy "patch"  to "/usr/bin"[/FONT]
 [FONT=&#26032;&#32048;&#26126;&#39636;]4.  tar xvfj  alsa-driver-1.0.24.xxxxxxx[/FONT]
 [FONT=&#26032;&#32048;&#26126;&#39636;]5.  cd  alsa-driver-1.0.24[/FONT]
 [FONT=&#26032;&#32048;&#26126;&#39636;]6.  ./configure --with-cards=hda-intel[/FONT]
 [FONT=&#26032;&#32048;&#26126;&#39636;]7.  make; make install[/FONT]
 [FONT=&#26032;&#32048;&#26126;&#39636;]8. reboot"

I understand most it, but I don't know what they mean by "patch" I have searched the entire folder for patch but nothing returned in the results. Maybe I have to download the correct file from somewhere else? I tried searching for it, but I have no luck finding it.
[/FONT]

 I had Ubuntu installed for over a month and never tried compiling software before until when I tried to install Realltek HD Audio Manager.

Where do I install the correct and most recent file and what do I do to install it?

---

### Post by don762003 on 2011-03-17
Any luck yet?

---

### Post by Silent Voice on 2011-03-24
that reply from a support was pretty helpful... it helped me to figure something out. i'm still new to linux, but i have a suggestion:
first of all,i noticed that there is nothing related to exact Realtek HD Audio Manager in that driver package...
actually, realtek just stole the alsa v 1.0.24 from official site and put it into their so-called linux driver pack... the only difference its that they written stupid and broken compilation script, that kills alsa after all, and put it into their so-called driver pack...
so, there is nothing new in that package, except for broken compilation script. you better go there [http://ubuntuforums.org/showthread.php?p=10595870&highlight=alsa+update#post10595870](http://ubuntuforums.org/showthread.php?p=10595870&highlight=alsa+update#post10595870) if ye wanna update your drivers.

---

