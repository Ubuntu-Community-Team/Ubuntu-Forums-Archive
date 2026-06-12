---
title: "Ubuntu 12.04 with Inspiron 1501 can't get wireless to work"
date: 2013-07-05
forum: Networking &amp; Wireless
---

### Post by Bryant777 on 2013-07-05
I can't get the wireless to work...
I tried sudo lshw -C network and got this:
house@house-Inspiron-1501:~$ ```
sudo lshw -C network
[sudo] password for house: 
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:c0200000-c0203fff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth1
       version: 02
       serial: 00:1c:23:9e:ce:f4
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10Mbit/s
       resources: irq:21 memory:c0300000-c0301fff
  *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@1:3.2
       logical name: wlan1
       serial: 68:7f:74:86:28:96
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=3.2.0-23-generic-pae firmware=0.29 ip=192.168.1.102 link=yes multicast=yes wireless=IEEE 802.11bgn


I also tried rfkill list all and got
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no 
```


So I tried a search in software center and only got bcm43 which was already installed.  But it still doesn't work!!!  I am using a wireless adapter right now.

---

### Post by wildmanne39 on 2013-07-05
Hi, please do:
```
sudo apt-get install --reinstall linux-firmware-nonfree
```
if you installed additional drivers you will need to remove them first.

Also your internal wireless card will not work as long as you have the usb adaptor plugged in.
Thanks

---

### Post by wildmanne39 on 2013-07-05
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by Bryant777 on 2013-07-05
```
[sudo] password for house: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-firmware-nonfree
```



Thanks!!!

---

### Post by Bryant777 on 2013-07-05
Do I need to repost?

---

### Post by wildmanne39 on 2013-07-05
Hi, did you have an internet connection when you ran that command?
Thanks

---

### Post by daighor on 2013-07-05
What a coincidence.  I actually just got wifi working on an Inspiron 1501 by following the instruction at this link:
[https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/218406](https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/218406)

Basically, using the command  [COLOR=#333333][FONT=Ubuntu]dmesg | egrep 'error|[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]irmware|[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]NET|wlan'   i found I the same error the person who posted it had,   
[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[/FONT][/COLOR]
Then I  followed the suggestion and ran 
[COLOR=#333333][FONT=Ubuntu]sudo apt-get install firmware-[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]b43-installer
[/FONT][/COLOR]
After firmware was updated, I rebooted the machine;  hit Fn+F2 to activate wifi on the 1501  and proceeded to set up the connection. 

I'm typing this reply on it, using wifi, right now.

Note that I'm a 2-day Linux user so I'm just regurgitating instruction.  But they worked for me.

---

### Post by Bryant777 on 2013-07-05
> **daighor said:**
> [COLOR=#333333][FONT=Ubuntu]
[/FONT][/COLOR]
Then I  followed the suggestion and ran 
[COLOR=#333333][FONT=Ubuntu]sudo apt-get install firmware-[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]b43-installer
[/FONT][/COLOR]


It didn't work for me.  Here is what happened.  I don't understand what it says.
```
house@house-Inspiron-1501:~$ sudo apt-get install firmware-b43-installer
[sudo] password for house: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
house@house-Inspiron-1501:~$ 


```

---

### Post by wildmanne39 on 2013-07-05
Hi, that command will do the same thing as the one I gave you except I do not believe it is complete.

That error is because you had software center and the terminal open at the same time.

If that is not the case reboot and then open the terminal and run the commands.
Thanks

---

### Post by Bryant777 on 2013-07-05
> **Wild Man said:**
> Hi, did you have an internet connection when you ran that command?
Thanks

I'm sorry. I couldn't remember so I ran it again with the adapter unplugged.  But in the interim, I decided to get all the updates (about 600).  I then unpluged and ran and got this:
```
house@house-Inspiron-1501:~$ sudo apt-get install --reinstall linux-firmware-nonfree
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
house@house-Inspiron-1501:~$ 

```

Bummer.  I probably shouldn't have updated but I was hoping an update might fix the problem.  What should I do?  This is not a mission critical laptop.  I can start all over if you say so.

thanks for taking the time to help me.

---

### Post by wildmanne39 on 2013-07-05
You have to be connected to the internet when you run the command, it has to dowload packages.
Thanks

---

### Post by Bryant777 on 2013-07-05
I connected adapter and tried again (after I realized that the command needed a connection).

```
house@house-Inspiron-1501:~$ sudo apt-get install --reinstall linux-firmware-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  linux-firmware-nonfree
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 3,952 kB of archives.
After this operation, 8,980 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise-updates/multiverse linux-firmware-nonfree all 1.11ubuntu2 [3,952 kB]
Fetched 3,952 kB in 44s (88.4 kB/s)                                            
Selecting previously unselected package linux-firmware-nonfree.
(Reading database ... 167853 files and directories currently installed.)
Unpacking linux-firmware-nonfree (from .../linux-firmware-nonfree_1.11ubuntu2_all.deb) ...
Setting up linux-firmware-nonfree (1.11ubuntu2) ...
house@house-Inspiron-1501:~$ 


```

---

### Post by Bryant777 on 2013-07-05
Yeah, that worked.  I am on the internal wifi card now.

Thanks so much, Wild Man!!!

---

### Post by wildmanne39 on 2013-07-05
Your welcome!
Enjoy!

---

