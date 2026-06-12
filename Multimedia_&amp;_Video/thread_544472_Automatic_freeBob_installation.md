---
title: "Automatic freeBob installation"
date: 2007-09-06
forum: Multimedia &amp; Video
---

### Post by CleverWilly on 2007-09-06
Hello!

I've been trying to install freeBob to my Ubuntu setup so that I can use M-Audio Ozonic audio interface. However, I'm a recent newbee and all guides on net are currently greek to me.

I wonder, is there is there some sort of freeBob installation programm like EasyUbuntu or Automatix?

That would make life much easier.

Thanks!

---

### Post by paulg on 2007-09-14
Enable the universe repositories if you haven't already done so. In terminal:

```
sudo aptitude install libfreebob0
```

That should install FreeBob and any dependencies you are missing. 

You can then grab a more recent version [here]("http://sourceforge.net/project/showfiles.php?group_id=117802&package_id=174085&release_id=493878"). 

Save the file somewhere you can find it (e.g. your home directory) and open a terminal:

```
cd /home/CleverWilly/whereisavedmyfile
sudo dpkg -i libfreebob0_1.0.3-1_i386.deb
```

Unfortunately I don't have a firewire/freebob device so I can't get you much farther than this. I do know that you need JACK (I highly advise you use JACK Control (qjackctrl) for starting the JACK daemon) and you need to set it to use FreeBoB (in qjackctrl there's a pull down box, by default it will be set to ALSA, there should be a FreeBob setting here...). 

I also think you need to have the Ubuntu Studio repositories to get a version of JACK for FreeBob. There is a version of JACK in the Universe repository for Feisty but I believe only the Ubuntu Studio version has been compiled for use with FreeBob - at least I vaguely recall reading that somewhere. You'll want the low-latency kernel from the Studio repositories anyway.

Best of luck, let me know how you progress and will try to help out if I can. I'm curious to hear how you make out with the MIDI aspect of the Ozonic.

---

### Post by rafafredd on 2007-12-05
Hi.

What about version 1.4? Would there be an automatic installation?

Otherwise, do you guys have any info about svn repositories and compiling? I would love to try the 1.4 version, as the current version won't work for me.

---

