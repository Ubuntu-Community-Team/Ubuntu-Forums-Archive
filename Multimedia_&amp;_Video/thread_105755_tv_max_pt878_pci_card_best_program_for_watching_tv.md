---
title: "tv max pt878 pci card best program for watching tv"
date: 2005-12-19
forum: Multimedia &amp; Video
---

### Post by Fibre on 2005-12-19
Is it possible for me to install the program that came with my tv card or is there one that can be use by all tv cards. I think Ubuntu  is picking it up right but with out get it connected up on my arial and having a program to run tv I can't use it.

I've install automatix, so those are the items other than what comes with ubuntu is installed on my pc.

Is there a site I can go to regarding this I havn't had much luck as yet in finding anything relating to this. Not quite sure what to type in I have tried some of the obvious type in's but having no idea of what programs I can use and there names it's a big of a struggle.

Thanks for any and all help I may get.

I have found tv timer television viewer and installed through synaptics but when i click on it nothing happens ?

in device manager it's only showing video and audion capture drivers but there's another 3 unknown so this could and probably is part of the problem although I would have thought the program would play anyway with or with out the card ?

---

### Post by 0okami on 2005-12-19
have you tried tvtime? 

to install, launch a terminal, and type:
sudo apt-get install tvtime

and then just run it by typing tvtime in the terminal.

---

### Post by Fibre on 2005-12-20
Ok I gave it a try Ookami and thank you for your reply - here is what happen

[COLOR="Red"]username@computer:~$ sudo apt-get install tvtime
Password:
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  lirc-x
Recommended packages:
  xmltv-util
The following NEW packages will be installed:
  tvtime
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/642kB of archives.
After unpacking 1782kB of additional disk space will be used.

Preconfiguring packages ...
Selecting previously deselected package tvtime.
(Reading database ... 91383 files and directories currently installed.)
Unpacking tvtime (from .../tvtime_1.0.1-2ubuntu1_i386.deb) ...
Setting up tvtime (1.0.1-2ubuntu1) ...

username@computer:~$ tvtime
Running tvtime 1.0.1.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/username/.tvtime/tvtime.xml
xvoutput: No XVIDEO port found which supports YUY2 images.

*** tvtime requires hardware YUY2 overlay support from your video card
*** driver.  If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: [http://gatos.souceforge.net/](http://gatos.souceforge.net/)
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.[/COLOR]

 I have a ATI Sapphire Radeon 9550 256mb agp card so I'd say it is capable. I just don't have the driver necessary to do it? I've updated my drivers for ATI but when i look at it it seems to be seen as a 128mb card which I'm trying to sought out on another thread I placed in this area relating to the agp card.

Being new to this there must be a way that I enter into the terminal, perhaps to get ?(apt-get)? at the address they have recommended or something like that.
I'm still very fuzzy when it comes to getting and running through the terminal or any other way involving more than a double click LOL.- I've only tried it a few times and don't really understand it yet.

[COLOR="Red"]For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: [http://gatos.souceforge.net/](http://gatos.souceforge.net/)
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.[/COLOR]

I would of thought all of that would be delt with through the tv card- but I think the agp card should have all I need. Everything runs fine on XP so there isn't any hardware problems other than the drivers needed by Ubuntu I'd have to guess and say.

Thank you for your help once again fellow Ubuntian. :)

---

