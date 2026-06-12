---
title: "Wired internet connection not working"
date: 2010-01-31
forum: Networking &amp; Wireless
---

### Post by nicbart9 on 2010-01-31
After installing UNR onto my dell mini 9 and downloading the correct drivers to enable wireless internet (using this site: [http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html) ), i decided to load ubuntu onto my brothers netbook. After the installation completed, i went to do complete the steps listed in the above article, however i was unable to connect to the internet using an ethernet wire. Any help would be appreciated. Thanks.

---

### Post by bkratz on 2010-01-31
> **nicbart9 said:**
> After installing UNR onto my dell mini 9 and downloading the correct drivers to enable wireless internet (using this site: [http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html) ), i decided to load ubuntu onto my brothers netbook. After the installation completed, i went to do complete the steps listed in the above article, however i was unable to connect to the internet using an ethernet wire. Any help would be appreciated. Thanks.

since the instructions you are following install the STA driver you can do the same without internet access by following the below:

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

See step 2 of the first half

---

### Post by nicbart9 on 2010-01-31
> **bkratz said:**
> since the instructions you are following install the STA driver you can do the same without internet access by following the below:

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

See step 2 of the first half

I went to step 2 of the first half and went to the LiveUSB instructions. When i finished with that it says to mark the bcmwl-kernel-source for installion, however it was already installed. So i rebooted again anyways and plugged in the cable and it still didn't connect to the internet.

I just checked the Hardware Drivers and the Broadcom Sta wireless driver shows up, however when i click on "Activate" and type in the admin password nothing happens even after i restarted it.

---

### Post by nicbart9 on 2010-01-31
UPDATE: The wired connection is now working. Thank you for your help.

---

### Post by bkratz on 2010-01-31
> **nicbart9 said:**
> UPDATE: The wired connection is now working. Thank you for your help.

Was there anything in particular you did to solve the wired part of the system, or just reboot? Anyway, please go to the thread tools and mark the thread as solved in case it helps someone else.

---

### Post by nicbart9 on 2010-01-31
The reboot solved the wired connection problem. However, i cannot activate the Broadcom STA wireless driver now via the Hardware Drivers utility.

---

### Post by bkratz on 2010-01-31
> **nicbart9 said:**
> The reboot solved the wired connection problem. However, i cannot activate the Broadcom STA wireless driver now via the Hardware Drivers utility.



What happens when you try to activate it?

---

### Post by nicbart9 on 2010-01-31
It asks for the password, then it says download/installing driver for about 2 seconds until it goes back to the original screen telling me that the driver is not activated.

---

### Post by bkratz on 2010-01-31
> **nicbart9 said:**
> It asks for the password, then it says download/installing driver for about 2 seconds until it goes back to the original screen telling me that the driver is not activated.

Can you go to the terminal (applications>>Accessories>>Terminal) and copy/paste the output of the following

sudo lshw -C network
(that is LSHW in lowercase and C in uppercase)

back here. Also do this with iwconfig.

---

### Post by nicbart9 on 2010-01-31
domenic@domenic-netbook:~$ sudo lshw -C network
*-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f0200000-f0203fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:24:e8:b2:53:fb
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.113 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:27 ioport:2000(size=256) memory:f0610000-f0610fff(prefetchable) memory:f0600000-f060ffff(prefetchable) memory:f0620000-f063ffff(prefetchable)

---

### Post by bkratz on 2010-01-31
See my post (#2) in this link, it has a link to a solution for your card.

[http://ubuntuforums.org/showthread.php?p=8751335#post8751335](http://ubuntuforums.org/showthread.php?p=8751335#post8751335)

Actually it is in post 7 of this link, but read the other one first

[http://ubuntuforums.org/showthread.php?p=8539988#post8539988](http://ubuntuforums.org/showthread.php?p=8539988#post8539988)

---

### Post by nicbart9 on 2010-01-31
> 2. [COLOR=DarkOrchid]ls /etc/modprobe.d | grep blacklist[/COLOR]
 
    This lists the contents of the */etc/modprobe.d* folder. Check the output of this command and make sure that there isn't a folder called *b43.conf, *bcm43.conf, *ssb.conf, or *wl.conf. If there is, rename the file by typing: [COLOR=DarkOrchid]sudo mv thefile.conf newnameofthefile.conf.backup[/COLOR]
 When i type in the first command i get:
```
blacklist-ath_pci.conf
blacklist-bcm43.conf
blacklist.conf
blacklist-firewire.conf
blacklist-framebuffer.conf
blacklist-modem.conf
blacklist-oss.conf
blacklist-watchdog.conf
```I have the file "blacklist-bcm43.conf" but when i try to rename it i get:
```
domenic@domenic-netbook:~$ sudo mv blacklist-bcm43.conf blacklist-abcd.conf.backup
mv: cannot stat `blacklist-bcm43.conf': No such file or directory
```What am i doing wrong?

---

### Post by bkratz on 2010-01-31
> **nicbart9 said:**
> When i type in the first command i get:
```
blacklist-ath_pci.conf
blacklist-bcm43.conf
blacklist.conf
blacklist-firewire.conf
blacklist-framebuffer.conf
blacklist-modem.conf
blacklist-oss.conf
blacklist-watchdog.conf
```I have the file "blacklist-bcm43.conf" but when i try to rename it i get:
```
domenic@domenic-netbook:~$ sudo mv blacklist-bcm43.conf blacklist-abcd.conf.backup
mv: cannot stat `blacklist-bcm43.conf': No such file or directory
```What am i doing wrong?


removed for wrong info

---

### Post by bkratz on 2010-01-31
> **nicbart9 said:**
> When i type in the first command i get:
```
blacklist-ath_pci.conf
blacklist-bcm43.conf
blacklist.conf
blacklist-firewire.conf
blacklist-framebuffer.conf
blacklist-modem.conf
blacklist-oss.conf
blacklist-watchdog.conf
```I have the file "blacklist-bcm43.conf" but when i try to rename it i get:
```
domenic@domenic-netbook:~$ sudo mv blacklist-bcm43.conf blacklist-abcd.conf.backup
mv: cannot stat `blacklist-bcm43.conf': No such file or directory
```What am i doing wrong?




duh!


WAIT A MINUTE, LET ME LOOK AT MINE

---

### Post by bkratz on 2010-01-31
I went ahead and looked at mine and the command appears to be correct. I don't know what happened, but I am google-ing. Here is the first one I found 

[http://www.linuxquestions.org/questions/linux-general-1/what-does-cp-cannot-stat-mean-640617/](http://www.linuxquestions.org/questions/linux-general-1/what-does-cp-cannot-stat-mean-640617/)

They are referring to cp rather than mv in that thread, but it really is sorta used the same way. I will continue to look and see what I can find. What it boils down to is I was wrong!

---

### Post by chili555 on 2010-01-31
> domenic@domenic-netbook:~$ sudo mv blacklist-bcm43.conf blacklist-abcd.conf.backupYou are in the wrong directory. Either do:```
cd /etc/modprobe.d
sudo mv blacklist-bcm43.conf blacklist-abcd.conf.backup
```Or else, you can give the complete path:```
domenic@domenic-netbook:~$ sudo mv /etc/modprobe.d/blacklist-bcm43.conf /etc/modprobe.d/blacklist-abcd.conf.backup
```> They are referring to cp rather than mv in that thread, but it really is the same thing. Not quite. mv is to rename a file and the original is now gone. cp is to copy a file, usually as a backup, and the original remains so you can work on it with the assurance that an easily recoverable backup is set aside. Recover by simply moving the backup to the original place:```
sudo mv file.conf.bak file.conf
```

---

### Post by bkratz on 2010-01-31
Darn I just figured it out!

 cd /etc/modprobe.d

---

### Post by nicbart9 on 2010-01-31
hmm... i tried all the steps listed on that one thread. rebooted and it still won't activate the driver. ](*,)

---

### Post by bkratz on 2010-01-31
Sorry to be such a problem, but can you do 
sudo lshw -C network
again and see if it still says unclaimed or if it says something to the effect of Driver..... in the field?


> **nicbart9 said:**
> domenic@domenic-netbook:~$ sudo lshw -C network
*-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f0200000-f0203fff


---

### Post by nicbart9 on 2010-01-31
It still says unclaimed. I've installed the netbook remix onto 2 other Dell mini9s with no problem and i find this so strange that i can't get it to work on this one.

---

### Post by bkratz on 2010-01-31
Found another interesting thread about your Dell mini9.
[http://www.ubuntumini.com/2009/11/installing-ubuntu-910-karmic-koala.html](http://www.ubuntumini.com/2009/11/installing-ubuntu-910-karmic-koala.html)
Basically later on it gives a pretty much equivalent methodology to what you already did, but it does mention making sure that it is turned on in the bios (section 5 is about wireless). Still looking.

See comments by
redDEAD said..

---

### Post by nicbart9 on 2010-02-01
I tried the steps outlined by redDEAD and it's still not working.

---

### Post by bkratz on 2010-02-01
Does the contents of

 sudo cat /etc/modules

show the line stating the term wl?

---

### Post by Iowan on 2010-02-01
Hmmm... Thread is marked as [SOLVED] 
Is it - or should it be marked as unsolved?

---

### Post by nicbart9 on 2010-02-01
> **bkratz said:**
> Does the contents of

 sudo cat /etc/modules

show the line stating the term wl?

It shows a line with "lp" and a line with "wl"


> **Iowan said:**
> Hmmm... Thread is marked as [SOLVED] 
Is it - or should it be marked as unsolved?

The problem of the wired internet not working is solved, so it's marked as [SOLVED] because of that.

---

### Post by nicbart9 on 2010-02-01
NOTE: I ran the same command on my working netbook and it only came up with the line "lp"

---

