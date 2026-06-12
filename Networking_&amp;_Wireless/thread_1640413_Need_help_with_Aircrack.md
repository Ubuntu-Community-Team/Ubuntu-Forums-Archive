---
title: "Need help with Aircrack"
date: 2010-12-07
forum: Networking &amp; Wireless
---

### Post by totallynew on 2010-12-07
i need some help to get this working and will pay for your time
basically have bg2200 bcm4318 wifi (working and connected to internet)
using ipw2200 i believe.
trying to aircrack and im stuck.
i'll pay first

---

### Post by alexfish on 2010-12-07
Don't think you will get a response to a Thread Title like this

members do it for free , but not as in free beer ....;)

Suggest looking at Sticky's at top of Networking and Wireless

then use Report button , to get Title changed

alexfish

---

### Post by uncaspi on 2010-12-07
No need to pay. Goto Broadcom site and download the latest STA driver. File
hybrid-portsrc_x86-32_v5.60.246.6.tar.gz
Unpack it and follow the instructions in the README.txt file.

Run this command from terminal sudo depmod -a
after sudo make install and then sudo modprobe wl
and your wireless should be working.

---

### Post by bkratz on 2010-12-07
> **uncaspi said:**
> No need to pay. Goto Broadcom site and download the latest STA driver. File
hybrid-portsrc_x86-32_v5.60.246.6.tar.gz
Unpack it and follow the instructions in the README.txt file.

Run this command from terminal sudo depmod -a
after sudo make install and then sudo modprobe wl
and your wireless should be working.

Aircrack will not work with the STA driver, the official Broadcom software does not support it.

---

### Post by totallynew on 2010-12-08
i realise its not the done thing but for a week and a good percentage of it actually trying searching and reading i'm getting no where
:popcorn:
just need a few hours of someones unhindered attention with me pasting outputs etc?
report sent for title change

---

### Post by totallynew on 2010-12-09
where is that special person who has time for me :D
i have looked at the guides and researched i guess its just too technical for me

---

### Post by totallynew on 2010-12-10
#-o:-\":sad::cry:

---

### Post by totallynew on 2010-12-11
i know your there

---

### Post by totallynew on 2010-12-12
anyone

---

### Post by alexfish on 2010-12-12
> **totallynew said:**
> anyone


hi

in the mean time 

have you looked here

[*Aircrack*-ng Newbie Guide for *Linux*]("http://www.google.co.uk/url?url=http://www.aircrack-ng.org/doku.php%3Fid%3Dnewbie_guide%23aircrack-ng_newbie_guide_for_linux&rct=j&q=how+to+aircrack+linux&usg=AFQjCNHBicTttzMKZyjSBckGIolFyoAiCw&sa=X&ei=k2IFTdSoMI6WhQfm05XtBw&ved=0CCsQygQ")&#8206;:

---

### Post by totallynew on 2010-12-13
Hi Alex, thx for the reply
reading and absorbing although i have braised over it before.
i.e the first port is to determin chipset
i've read the intel proset bg2200 is ok and uses broadcom 4318 chipset. ?
my driver is ip22w something. probably unpatched 
the index of patched drivers in aircrack-ng.com don't seem to have a download link to get them . when clicking on them i just get a browser with what looks like "code"?

---

### Post by alexfish on 2010-12-13
Hi

don't no if on write track ,

say if looking for specific driver

Example

on the site :

[http://www.aircrack-ng.org/doku.php?id=install_drivers](http://www.aircrack-ng.org/doku.php?id=install_drivers)

then in the list of drivers

if a driver is selected it takes you to a page and gives instructions as how to install

IE this page gives instructions

[http://www.aircrack-ng.org/doku.php?id=ipw2200&DokuWiki=37019891a858ce4b625c009248f991fd](http://www.aircrack-ng.org/doku.php?id=ipw2200&DokuWiki=37019891a858ce4b625c009248f991fd)


when dowloading from the terminal 

open the terminal and set up as root

Code:

sudo su 


then follow instructions 

note the wget ..http etc  this is the command to get the download from the location 

alexfish

---

### Post by totallynew on 2010-12-13
ok from the aircrack-ng.com it directs you to here for patched drivers
clicking on it doesn't give a get command etc
[http://patches.aircrack-ng.org/](http://patches.aircrack-ng.org/)

---

### Post by alexfish on 2010-12-13
MM?

best I can do is direct you to here

[HOWTO: Aircrack-NG (Simple Guide)]("http://ubuntuforums.org/showthread.php?t=528276")

---

