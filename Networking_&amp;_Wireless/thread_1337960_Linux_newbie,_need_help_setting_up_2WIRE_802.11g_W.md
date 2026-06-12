---
title: "Linux newbie, need help setting up 2WIRE 802.11g Wireless USB Adapter"
date: 2009-11-25
forum: Networking &amp; Wireless
---

### Post by Asbian on 2009-11-25
I've been trying to convert from windows to ubuntu for months now, and the only reason I havn't, is because I can't figure out how to setup my wireless card (2WIRE 802.11g wireless usb adapter). I've found a few guides that tell how to do it but they were too complicated for me and I didn't understand them, so I had no luck. Could anyone give me some very BASIC instructions on how to set this up? If it makes a difference my computer is a Dell Dimension 2400. (I want to setup the newest version of ubuntu which I guess is currently 9.10)

---

### Post by Asbian on 2009-11-26
Ok. I tried using
```
ndiswrapper
```
in terminal and it said something about ndiswrapper not being installed. And it told me to type
```
sudo apt-get install ndiswrapper
```
Or something similar to that, so I did. When it asked for a password I just typed my account password, which seemed to work. I got a reply saying something like "ndiswrapper is not in install package". I also tried synaptic which looked promising, but I couldn't figure it out. Another tutorial told me to use ndisgtk, but it was less successful then ndiswrapper.

---

### Post by Asbian on 2009-11-26
Bump

---

### Post by bkratz on 2009-11-27
Ndisgtk is really the easiest way, the are two file dependencies which are automatically loaded ---ndswrapper-utils-1.9 and ndiswrapper-common: would be happy to help if you explain the problem you are having.

---

### Post by Asbian on 2009-11-29
> **bkratz said:**
> Ndisgtk is really the easiest way, the are two file dependencies which are automatically loaded ---ndswrapper-utils-1.9 and ndiswrapper-common: would be happy to help if you explain the problem you are having.

Ok, I have no idea what Ndisgtk or anything really on ubuntu is yet, (trying to learn), but I tried typing it in terminal and got similar results as those with ndiswrapper

---

### Post by bkratz on 2009-11-29
> **Asbian said:**
> Ok, I have no idea what Ndisgtk or anything really on ubuntu is yet, (trying to learn), but I tried typing it in terminal and got similar results as those with ndiswrapper



Ndiswrapper is used with Windows type drivers (the .inf and .sys files only)  Do you have any drivers?

---

### Post by bkratz on 2009-11-29
Actually please go to applications---accessories-- terminal  a small screen will come up

type in 

lsusb

(that is LSUSB in lowercase)

Copy and paste what you receive here it should tell us the chipset used.

---

### Post by Asbian on 2009-12-05
Sorry I'm responding so slowly, havn't had time to get on my computer for a few days. I typed lsusb and here's the results:

```
tyler@ubuntu:~$ lsusb
Bus 001 Device 002: ID 1630:0005  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 046d:c308 Logitech, Inc. Internet Navigator Keyboard
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04fc:05d8 Sunplus Technology Co., Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
tyler@ubuntu:~$
```

I'm pretty sure I couldn't mess this up, even if I tried :p
I entered terminal, I typed lsusb (LSUSB), and hit my enter key. Then I copied the text into the text editor I found under accessories, and saved it to my flashdrive, then I started windows (dual boot), and opened the internet. Lol.

Oh, and as for the question about me having drivers: I do have the driver for the adapter but it's windows drivers.

---

### Post by Asbian on 2009-12-05
Oh, and as for the question whether I have drivers, I do but it's a windows driver.

---

### Post by bkratz on 2009-12-06
> **Asbian said:**
> Sorry I'm responding so slowly, havn't had time to get on my computer for a few days. I typed lsusb and here's the results:

```
tyler@ubuntu:~$ lsusb
Bus 001 Device 002: ID 1630:0005  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 046d:c308 Logitech, Inc. Internet Navigator Keyboard
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04fc:05d8 Sunplus Technology Co., Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
tyler@ubuntu:~$
```

I'm pretty sure I couldn't mess this up, even if I tried :p
I entered terminal, I typed lsusb (LSUSB), and hit my enter key. Then I copied the text into the text editor I found under accessories, and saved it to my flashdrive, then I started windows (dual boot), and opened the internet. Lol.

Oh, and as for the question about me having drivers: I do have the driver for the adapter but it's windows drivers.



Bus 001 device 002 is the 2-Wire usb dongle.  Searching for that shows this link

[http://ubuntuforums.org/showthread.php?t=707972](http://ubuntuforums.org/showthread.php?t=707972)

Which seems a little old but still looks useful.  Good Luck

---

### Post by Asbian on 2009-12-06
> **bkratz said:**
> Bus 001 device 002 is the 2-Wire usb dongle.  Searching for that shows this link

[http://ubuntuforums.org/showthread.php?t=707972](http://ubuntuforums.org/showthread.php?t=707972)

Which seems a little old but still looks useful.  Good Luck

Thanks, I'll try that.

---

### Post by Asbian on 2009-12-06
Ok, so I tried using that thread you suggested and didn't come up with very productive results:

```
tyler@ubuntu:~$ sudo ndiswrapper -i WlanUIG.inf
[sudo] password for tyler: 
sudo: ndiswrapper: command not found
tyler@ubuntu:~$ ndiswrapper -l
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
ndiswrapper: command not found
tyler@ubuntu:~$
```

and then:

```
tyler@ubuntu:~$ ndiswrapper -l
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
ndiswrapper: command not found
tyler@ubuntu:~$ sudo apt-get install ndiswrapper-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper-common
tyler@ubuntu:~$ sudo apt-get install ndiswrapper-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper-common
tyler@ubuntu:~$
```

---

### Post by bkratz on 2009-12-06
It doesn't seem that you have loaded ndiswrapper does it?  Let's do this the easy way (about time huh)

go to System--Administration-Synaptic package Manager
put in you password
Press the reload button
Do a quick search for Ndis
Tick---Ndisgtk

It will automatically select the two other ndiswrapper dependencies

You now will have the files you wanted to try

since you have Ndisgtk you can try to go to 
System---Administration---Windows wireless drivers and "point" at the .inf file you got from you CD (put it and the .sys file somewhere like your home directory for ease of finding)
Follow the directions, I think you should be able to understand what to do from here.

If worse comes to worst you at least will have the necessary files to do what you were trying to do from the other thread!

Good Luck

---

### Post by Asbian on 2009-12-06
Ok. first of all, before I tell you how it went, I'll point out when I hit reload in the syptanaptic (ignore spelling) thing, I got an error screen:

```
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.
```

So I quick-searched "ndis" anway, and got 0 results. :(

---

### Post by bkratz on 2009-12-06
If you go back to Synaptic Package Manager  and press settings--repositories 

What shows on the screen

The first two entires should be ticked at least I have four since I downloaded some flash software, also remove the tick from CD rom
Also what is listed under download from:
 I download from the uchicago ( I assume it is the University of Chicago, but really don't know) repository since it is phyically close to me.

---

