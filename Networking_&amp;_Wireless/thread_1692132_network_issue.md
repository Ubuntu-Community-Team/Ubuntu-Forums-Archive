---
title: "network issue"
date: 2011-02-21
forum: Networking &amp; Wireless
---

### Post by ubun2warrior on 2011-02-21
hi

i have 3 comps(running ubuntu 10.04) and a laptop(running vista sp2). i have installed samba on all ubuntu comps. i have a printer attached to one of the comps and it has been shared also the internet connection on that comp has been shared. all the computers are connected using lan cables through an ethernet switch. i also have a wireless router which is connected to the ethernet switch.

I am able to view all the comps on the network except the laptop running vista. all the desktops are visible on the network and are able to print and share files on the network and also connect to the internet. 

the laptop running vista can connect to the internet but its not visible on the network and nor can it share files across the network or access the printer.

all the systems have a static ip.

plz help

rgds

---

### Post by ubun2warrior on 2011-02-21
hi

any suggestions !!

rgds

---

### Post by Keiran230 on 2011-02-21
Try changing the workgroup. If I recall, XP and samba default to MSHOME as the workgroup, but Vista and 7 default to WORKGROUP. You can change this in computer properties.

---

### Post by ubun2warrior on 2011-02-21
hi

i tried MSHOME, did not work..

rgds

---

### Post by frankduffey on 2011-02-22
> **ubun2warrior said:**
> hi

i have 3 comps(running ubuntu 10.04) and a laptop(running vista sp2). i have installed samba on all ubuntu comps. i have a printer attached to one of the comps and it has been shared also the internet connection on that comp has been shared. all the computers are connected using lan cables through an ethernet switch. i also have a wireless router which is connected to the ethernet switch.

I am able to view all the comps on the network except the laptop running vista. all the desktops are visible on the network and are able to print and share files on the network and also connect to the internet. 

the laptop running vista can connect to the internet but its not visible on the network and nor can it share files across the network or access the printer.

all the systems have a static ip.

plz help

rgds
<h3><p>
Frank Duffey
Owner Franks Computers
Gainesville,Fl 32605
  I did get my wireless network working install ndiswrapper do a search onm this forum there are instructions on how to install from the terminal or using package manager which is the perfered method I am a A+ certifited tech nican and former Computer business owner however I am new to Linix also so I am a fast learner having 20 yrs computer exp[erence I love this os oit gives the uswer more control of the system and the alility to run a server with a dsl connection. If you are runnin g windows 7 or XP go to the CMD then run ipconfig/all write down all the dns server info as well as any infomation aboiut your neytwprook card ndiswarpper will strighten out the problem be sure to blacklist the broadcomm 43xx network driver see info in the forumn on terminmal commands to use blacklisting of network card or you will not see the driver that you found on the network. You can also run nBASP to remove and install network drivers be sure to download the correct driver for your system and save it on your home folders. I hope this hekps I have spent mnay hours doing research on this topic. I am also network norvell certified I had 2 technicans working for me at Tampa Bay Communications Inc where I started a computer business in 1995 so you can see that I have been in the IT indistry fpr many years I was forced to retire due to na brain tumor and I am now on SSDI. I still do networks part time as well as new windows and linux systems now. I can order a system with no os and load :)ubnuntu 10.10 I do have 11.4 but so  there is no support for a windows install I am still running windows 7 with a dual boot Goodd Luckl Let me know if this helps you out?.</h3></p>

---

### Post by ubun2warrior on 2011-02-22
hi

i have tried the above methods. it did not work out, i don't think there is any problem with my wireless lan or any hardware stuff. its just the configuration thats causing the pain..

rgds

---

### Post by ubun2warrior on 2011-02-22
hi 

plz suggest some method...

rgds

---

### Post by ubun2warrior on 2011-02-23
someone plz help :)

---

### Post by Morbius1 on 2011-02-23
Please post the output of the following command and see if it lists the Vista machine:
```
smbtree
```If you have a firewall enabled on Vista then temporarily disable it and try smbtree again.

---

### Post by ubun2warrior on 2011-02-23
> **Morbius1 said:**
> Please post the output of the following command and see if it lists the Vista machine:
```
smbtree
```If you have a firewall enabled on Vista then temporarily disable it and try smbtree again.

hi

there is no output for smbtree. it just asks for the password then returns back the prompt. no output. i tried with vista firewall disabled as well.

rgds

---

### Post by ubun2warrior on 2011-02-24
hi

any clues?? what next to do ??

rgds

---

### Post by ubun2warrior on 2011-02-25
please help !!!

:(

---

### Post by ubun2warrior on 2011-04-23
hi

i have installed windows 7 on my laptop and again i try to detect network printer and still no success.

kindly suggest some solution for this

ubun2warrior

---

### Post by ubun2warrior on 2011-04-23
hi

i somehow managed to get it working.
had to make some changes in /etc/samba/smb.conf

wins support was no so changed it to yes and also changed guest ok to yes

now i am able to use the shared printer!!!

---

