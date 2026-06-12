---
title: "succcessful install Dick Smith USB wireless adapter"
date: 2009-10-03
forum: Networking &amp; Wireless
---

### Post by pdc on 2009-10-03
I trust it is okay to report this: these wireless USB adapters are sold by Dick Smith in Australasia: $A30 and $NZ40 currently;

lsusb gives

> ID 148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapter


seems this is the rt73 driver; I was not sure from google searching on 

> ubuntu rt73 wireless install how what exactly to do

[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73)

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29)

so I downloaded 2009_0713_RT73_Linux_STA_Drv1.1.0.3.zip into directory Downloads

one needs dos2unix at one stage so worthwhile doing it now:

> sudo aptitude install tofrodos

and one needs a directory /etc/Wireless/RT73STA/ so I made it by 

> cd /etc
> sudo mkdir Wireless
> cd Wireless
> sudo mkdir RT73STA

then I opened a second terminal and started to install the RT73

> cd Downloads
> unzip 2009_0713_RT73_Linux_STA_Drv1.1.0.3.zip

this gives a directory 2009_0713_RT73_Linux_STA_Drv1.1.0.3          ......... so ............ 
> cd 2009_0713_RT73_Linux_STA_Drv1.1.0.3and this gives a directory Module so
> cd Module these directories are different to those specified in the Ralink README hence I spelt out what I did

then from the README for a 2.6 kernel

> cp Makefile.6  ./Makefile
> make all
> sudo make install
> sudo cp rt73.bin /etc/Wireless/RT73STA/
> dos2unix rt73sta.dat

the README says to check the file is binary so I did 

> gedit rt73sta.datand it seemed to have been converted to binary so all was well

then 

> cp rt73sta.dat  /etc/Wireless/RT73STA/rt73sta.dat
> /sbin/insmod rt73.ko
> /sbin/ifconfig rausb0 inet YOUR_IP up

with > /sbin/iwconfig and > sbin/iwlist scan I could see things had worked; I right-clicked on Network Manager to add a new wireless connection; and then rebooted; I was pleased to see it had picked up our wireless access point we run off a wired router; and could so get to the internet; I hope this may be of help to someone; I understand rt73 is in the kernel, so I may not have needed all these steps; happy for someone to correct me as needed

---

### Post by stinger30au on 2009-10-03
cool

thanks for the info

---

### Post by what, what? on 2010-01-11
i have problems at the cd modules part, it says no file or directory

---

### Post by pdc on 2010-01-11
when you get to the section 

> cd 2009_0713_RT73_Linux_STA_Drv1.1.0.3

if you type in 

> ls

this command asks the system to list what is in there

tell us by copy and paste what you get

(the reason is I guess I must have had a directory called 

> Module

after I had issued the top command)

let's see what directories you have listed

You will note that my post said

> cd Module

and you write

> cd modules

You should be looking for a directory called

> Module

do you think instead you are looking for a directory called

> modules

linux is very particular about spelling

---

### Post by what, what? on 2010-01-11
> **pdc said:**
> when you get to the section 



if you type in 



this command asks the system to list what is in there

tell us by copy and paste what you get

(the reason is I guess I must have had a directory called 



after I had issued the top command)

let's see what directories you have listed

You will note that my post said



and you write



You should be looking for a directory called



do you think instead you are looking for a directory called



linux is very particular about spelling


After doing the cd and the unzipped thing, i got :  autorun.inf  setup

Thats all. Did i do it wrong? And i did do module, not modules.

---

### Post by pdc on 2010-01-11
OK

just booted up the laptop with 9.04 on i; and using the Dick Smith rt73 USB adapter back to our WAP

I used directory 

> Downloads for this so if I ask what is in that directory I get

> pdc@pdc-laptop:~/Downloads$ ls
2009_0713_RT73_Linux_STA_Drv1.1.0.3      
2009_0713_RT73_Linux_STA_Drv1.1.0.3.zip  

so I unzipped the original .zip file and got the 2009_0713_RT73_Linux_STA_Drv1.1.0.3 directory

tell us what you get what you get if you issue the command

> ls

whilst in the directory that you put 2009_0713_RT73_Linux_STA_Drv1.1.0.3.zip

---

### Post by what, what? on 2010-01-11
> **pdc said:**
> OK

just booted up the laptop with 9.04 on i; and using the Dick Smith rt73 USB adapter back to our WAP

I used directory 

 for this so if I ask what is in that directory I get



so I unzipped the original .zip file and got the 2009_0713_RT73_Linux_STA_Drv1.1.0.3 directory

tell us what you get what you get if you issue the command



whilst in the directory that you put 2009_0713_RT73_Linux_STA_Drv1.1.0.3.zip


So I have the zip and other thing in my downloads, i have: 

```
jake@jake-laptop:~/Downloads$ ls
WUSB54GCV3_USCAN.4.9.9047.0-ship-QFE.Stable.DS
WUSB54GCV3_USCAN.4.9.9047.0-ship-QFE.Stable.DS.zip

```

And when I do```
cd WUSB54GCV3_USCAN.4.9.9047.0-ship-QFE.Stable.DS
```

It takes me to it, when I type ```
ls
```

I get ```
jake@jake-laptop:~/Downloads/WUSB54GCV3_USCAN.4.9.9047.0-ship-QFE.Stable.DS$ ls
autorun.inf  setup
``` That is all i get from it.

---

### Post by pdc on 2010-01-11
you want to configure a USB device, so that it can connect to a wireless network?

If so, can you plug this device into a USB port on a computer running linux (I know it is not configured yet)

and type in a terminal

> lsusb

and tell us what you get by copying and pasting the result

---

### Post by what, what? on 2010-01-11
> **pdc said:**
> you want to configure a USB device, so that it can connect to a wireless network?

If so, can you plug this device into a USB port on a computer running linux (I know it is not configured yet)

and type in a terminal



and tell us what you get by copying and pasting the result


```
jake@jake-laptop:~$ lsusb
Bus 002 Device 002: ID 0461:4d0f Primax Electronics, Ltd 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 1737:0077 Linksys 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by pdc on 2010-01-11
OK; 

what I posted was how to use the ralink rt73 driver to get a device running;

You want to configure a different device;

seems from this post

[http://newyork.ubuntuforums.org/showthread.php?t=1155941&highlight=WUSB54GCv3](http://newyork.ubuntuforums.org/showthread.php?t=1155941&highlight=WUSB54GCv3)

that you want the rt2870 drivers; they are different;

the above listing in post #2 tells how the guy got it working; you should try that; best to copy and paste all commands from his post into your terminal

(I use the Edit at the top of a terminal and select copy or paste from the menu as my fingers don't do shift-control-c very well)

---

### Post by what, what? on 2010-01-11
> **pdc said:**
> OK; 

what I posted was how to use the ralink rt73 driver to get a device running;

You want to configure a different device;

seems from this post

[http://newyork.ubuntuforums.org/showthread.php?t=1155941&highlight=WUSB54GCv3](http://newyork.ubuntuforums.org/showthread.php?t=1155941&highlight=WUSB54GCv3)

that you want the rt2870 drivers; they are different;

the above listing in post #2 tells how the guy got it working; you should try that; best to copy and paste all commands from his post into your terminal

(I use the Edit at the top of a terminal and select copy or paste from the menu as my fingers don't do shift-control-c very well)

would you happen to nkow why when i do 
cp -p /lib/modules/`uname -r`/kernel/drivers/net/wireless/rt2870sta.ko /lib/modules/`uname -r`/updates/ 

I get:  ```
70sta.ko': No such file or directory
```

---

### Post by what, what? on 2010-01-13
bumpE

---

### Post by sinkyboy2000 on 2010-01-17
When I type dos2unix rt73sta.dat it tells me dos2unix is not installed and that I can install it by typing apt-get install tofrodos.
 
But when I type that it tells me 
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: unable to lock the administration directory (/var/lib/dpkg/), are you root
 
Help would be appreciated.

---

### Post by pdc on 2010-01-17
on ubuntu, you need "root" or "sudo" privileges to do things to your computer

so the command would be 

> sudo apt-get install tofrodos

you will be asked for your sudo password; if you type that into the terminal, and press enter, things ......... should  ..... happen

---

### Post by sinkyboy2000 on 2010-01-18
> **pdc said:**
> on ubuntu, you need "root" or "sudo" privileges to do things to your computer
 
so the command would be 
 
 
 
you will be asked for your sudo password; if you type that into the terminal, and press enter, things ......... should ..... happen
 
Thanks for that.  However, I did actually type "sudo" first and this was the error messageI got.  I should also have said that I am using xubuntu 9.10, not Ubuntu (if that makes a diffence).

---

### Post by sinkyboy2000 on 2010-01-18
OK.  I used a windows machine to convert the .dat file to unix using an online converter, so I hope that's done the trick.  
 
But when I type  
 
/sbin/insmod rt73.ko 
 
I'm told there's no such file or directory.  When i list the files in the directory that seems to e right/  Any ideas?

---

