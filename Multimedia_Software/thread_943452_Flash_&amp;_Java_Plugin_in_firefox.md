---
title: "Flash &amp; Java Plugin in firefox"
date: 2008-10-10
forum: Multimedia Software
---

### Post by kagimaro on 2008-10-10
Hello everyone,

Am having a problem with Flash & Java plugins in firefox
when i go to [www.f1.com](www.f1.com) with the flash enabled the right panel of the website just appear plain white.
But when i disable the flash plugin i can see it.

I included the picture ... hope to find a solution

I just looked everywhere on the forums and other websites, but it seems am the only 1 who had this problem

[IMG]http://i36.tinypic.com/111rw50.jpg[/IMG]

---

### Post by baizon on 2008-10-10
Do you got the flashplugin-nonfree package?

---

### Post by kagimaro on 2008-10-10
Yes .. the flashplugin-nonfree package is currently installed .. and its working fine as you can see the above black area on the pic is flash ..

Java & Flash are installed ..
This problem exist for me in Ubuntu & Mint.
I tried re-installing the OS .. removing and re-installing Flash & Java .. but nothing seems to work

---

### Post by minky311 on 2008-10-10
Try installing flash player 10 beta which seems to solve a lot of the problems with flash on linux.
Here are instructions.
The First thing you should do is open up synaptic package manager system->administration->synaptic package manager and search for flash player non free and uninstall it. Also search for libflashsupport and uninstall it if you have it. It is no longer needed in flash player 10.

Go here [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html) scroll down to the bottom and download the plugin for linux in tar.gz format.Save it to the desktop. Right click it and select extract here.

Next Open up a terminal applications->accessories->terminal and do the following one at a time.
Code:
```

cd Desktop
cd install_flash_player_10_linux
./flashplayer-installer
```

Then press enter to install. Make sure any browsers you have open are closed.

---

### Post by baizon on 2008-10-11
...or install the intrepid [http://packages.ubuntu.com/intrepid/flashplugin-nonfree]("http://packages.ubuntu.com/intrepid/flashplugin-nonfree")

---

### Post by kagimaro on 2008-10-11
Thank you all for responding :) I really appreciate it

minky311, your solution really works!
I just installed ubuntu .. and installed the necessary codecs i need then installed java & flash 10 following your steps
Its working like a charm now .. Thank you

---

### Post by Ameneon on 2008-10-11
Oh the joy if this finally sorts out the Flash hell in Ubuntu. If there ever was one single issue aside from the somewhat mediocre selection of commercial games for Linux that could make me consider going back to Windows, Flash-lag would be it. Now let's just hope something else doesn't come in place of it..

---

### Post by BoneSaw on 2008-10-12
does anyone know why myspace players might not work?

do i just have to deal with the crashes caused by 9 or wait till myspace upgrades to be compatible?

---

