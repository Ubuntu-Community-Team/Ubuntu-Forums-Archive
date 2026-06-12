---
title: "Flash Player 9 architecture not supported"
date: 2007-06-03
forum: Multimedia &amp; Video
---

### Post by pfwd.tech on 2007-06-03
Hi, i am trying to install flash player 9 and im hitting a brick wall.
This is what im getting:
```
pete@pfwd:~$ cd /usr/src
pete@pfwd:/usr/src$ cd install_flash_player_9_linux/
pete@pfwd:/usr/src/install_flash_player_9_linux$ ./flashplayer-installer 
ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer
```.

I have installed the 32 bit compatibility libraries by doing:
```
sudo apt-get install ia32-libs
```Not sure what i should do.
Any one know where to go from here?

<edit> Sorry forgot to mention im using an intel e6400 cpu and a p5b mobo

---

### Post by pfwd.tech on 2007-06-03
I have tired to get the plugin using add and remove and it says the following:
> Macromedia Flash plugin cannot be installed on your computer type (amd64). Either the application requires special hardware features or the vendor decided to not support your computer type.

There must be a way to get flash working on x64

---

### Post by 1993cb7 on 2007-06-04
Yes i have the same problem....i need to get macromedia installed and i dl the .exe and i cant seem to figure it out...im new to Linux and not too good with the terminal yet but im good and copying and pasting lol...

so im looking forward to some responses!

---

### Post by pfwd.tech on 2007-06-04
Yeah there must be a way around it.  Surely somone out there has had this problem and fixed it!!

---

### Post by 1993cb7 on 2007-06-04
So when you browse the net you get that warning about needing plugins right?

that crap is so annoying....damn ive got a lot to learn...

anyone out there!?:(

---

### Post by pfwd.tech on 2007-06-04
Yep thats what i get. There must be a fix out there

---

### Post by pfwd.tech on 2007-06-04
This is where im getting the flash installer from 
[http://www.adobe.com/shockwave/download/index.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/index.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)

---

### Post by pfwd.tech on 2007-06-05
> **1993cb7 said:**
> So when you browse the net you get that warning about needing plugins right?

that crap is so annoying....damn ive got a lot to learn...

anyone out there!?:(

I have discovered a way to get flash working by using 32bit 
Please read this thread and download the ndiswrapper installer for flash (its the first post)
[http://ubuntuforums.org/showthread.php?t=425672&highlight=flash](http://ubuntuforums.org/showthread.php?t=425672&highlight=flash)
Ive got it working fine on my machine.
Intel E6400 Ubuntu amd64  
Hope this helps

---

### Post by wesswei on 2008-04-09
just in case anyone comes here looking for this fix, it's not an ndiswrapper, it's nspluginwrapper for compatible browsers. ndiswrapper is generally windows compatibility for wireless networking devices.

---

