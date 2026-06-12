---
title: "Problem with Conceptronic wireless card C300Ri with chipset RT3062F in ubuntu 11.04"
date: 2011-05-27
forum: Networking &amp; Wireless
---

### Post by Alfiran on 2011-05-27
Hello all,

I'm a rookie with linux and this is my first post here so if this isn't the right "subforum", please advice.

Well, recently I just bought a new wireless card for my PC, a conceptronic C300Ri with 11n suport (300 Mbps) with chipset Ralink RT3062F. It works really good in Windows7 64bits but I'm trying to make it works in ubuntu 11.04 because I want to migrate to it.

Ubuntu doesn't recognize it by itself so I downloaded the driver from ralink website [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2) in a TGZ file. I extract the files to a "folder" in desktop and follow the steps:

./configure
sudo make
sudo make install

The first error message is that the file "configure" doesn't exist so I procced with the next two comands which they seem to work properly. Then I reboot the system but the wireless card doesn't work.

I will appreciate any light about it

cheers

---

### Post by lprofil on 2011-08-15
Hey Alfiran,

i just bought the same Conceptronic card. On the box it says **Conceptronic 300Mbps 11n**. 
If i am successful installing the driver i will post my solution here. 

> **Alfiran said:**
>  I extract the files to a "folder" in desktop and follow the steps:
./configure
sudo make
sudo make install


[LIST]
[*]Did you follow the instructions and especially **step 2** in the 
README_STA_pci file?
[*]And maybe even more important: did you change the default chipset
[/LIST]


from
CHIPSET = 3562
to
CHIPSET = 3062
?


1> $tar -xvzf DPB_RT2860_Linux_STA_x.x.x.x.tgz
    go to "./DPB_RT2860_Linux_STA_x.x.x.x" directory.
    
**2> In Makefile**
	 set the "MODE = STA" in Makefile and chose the TARGET to Linux by set "TARGET = LINUX"
	 define the linux kernel source include file path LINUX_SRC
	 modify to meet your need.
...

A good hint for me was the [link to the Ralink]("http://www.ralinktech.com/support.php?s=2") site.
Thanks for that.

This link might also be helpfull for you:
[http://ubuntuforums.org/showthread.php?t=1654876&page=2](http://ubuntuforums.org/showthread.php?t=1654876&page=2)
I found it googeling for the extracted files foldername:
DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217

/lprofil

---

### Post by Alfiran on 2011-08-17
Thank you very much lprofil. I found some threads too, here in the forums but they looked a bit complicated. I'll try again and let you know. 

Thank you again.

Regards

---

