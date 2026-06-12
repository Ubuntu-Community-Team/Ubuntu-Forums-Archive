---
title: "troubleshooting wireless connection problem broadcom bcm4311"
date: 2013-03-28
forum: Networking &amp; Wireless
---

### Post by prodigalson7777 on 2013-03-28
Hi i am new to ubuntu and computers in general.  I am having trouble getting ubuntu to recognize my wireless card.  Any help is appreciated.

[FONT=arial]1. The computer i am using is a dell inspiron 1520 with a core2duo.  I found some documentation on the web detailing problems recognizing my wireless card which is the Broadcom BCM4311.  There seems to be several different "fixes" but it seems to be a common issue.  I found some info that gives methods for installing different drivers but it's over my head.  [http://ubuntuforums.org/showthread.php?t=1745437](http://ubuntuforums.org/showthread.php?t=1745437)[/FONT]
[FONT=arial]2. 4GB Ram[/FONT]
[FONT=arial]3. Brodcom BCM4311 wireless card[/FONT]
[FONT=arial]4. Dual boot HD install using wubi[/FONT]
[FONT=arial]5. 32k[/FONT]
[FONT=arial]
```
[FONT=Verdana]mike@ubuntu:~$ sudo lshw -C network [/FONT]
```[/FONT]```

[sudo] password for mike: 
Sorry, try again. 
[sudo] password for mike: 
PCI (sysfs)   
  *-network                
       description: Network controller 
       product: BCM4311 802.11b/g WLAN 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:0c:00.0 
       version: 01 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list 
       configuration: driver=b43-pci-bridge latency=0 
       resources: irq:17 memory:fe8fc000-fe8fffff 
  *-network 
       description: Ethernet interface 
       product: BCM4401-B0 100Base-TX 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:03:00.0 
       logical name: eth0 
       version: 02 
       serial: 00:1c:23:8b:d7:22 
       size: 10Mbit/s 
       capacity: 100Mbit/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10Mbit/s 
       resources: irq:17 memory:fe5fe000-fe5fffff 
mike@ubuntu:~$ 
mike@ubuntu:~$ nm-tool 


NetworkManager Tool 


State: disconnected 


- Device: eth0 ----------------------------------------------------------------- 
  Type:              Wired 
  Driver:            b44 
  State:             unavailable 
  Default:           no 
  HW Address:        00:1C:23:8B:D7:22 


  Capabilities: 
    Carrier Detect:  yes 


  Wired Properties 
    Carrier:         off 



```[FONT=arial]
[/FONT]

---

### Post by kc1di on 2013-03-29
Hello prodigalson7777 and welcome to Ubuntu and Linux,

Sorry your having problems, Broadcom cards can be a little tricky.  but the good news is once they are setup they work well. 

[here is a page]("http://askubuntu.com/questions/38327/how-can-i-get-broadcom-bcm4311-wireless-working") that should get you going if you follow it.

remember if you installed the STA driver you'll have to uninstall it first.

---

### Post by prodigalson7777 on 2013-04-06
Hello Dave,

Thank you for getting back to me.  I have made some progress in identifying my problems.  I do not have access to an ethernet connection so i cannot install the broadcom drivers via a wired connection.  I am running Ubuntu under a dual boot with Windows which has a wireless conncection.  So, I have decided the best idea is to create a directory and download the appropriate drivers into the folder and then install them in Ubuntu via command line.  Being that i am a green blooded NOOB I am not sure where i would go to download the appropriate drivers for the broadcom bcm4311.  Any help would be appreciated.  

Thanks Again

---

### Post by wildmanne39 on 2013-04-06
Hi, Download the b43 zip file to a flash drive then drag and drop the file to your ubuntu desktop. Right-click it and select Extract Here. Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
Thanks
[ATTACH]241050[/ATTACH]

---

### Post by mörgæs on 2013-04-07
Moved to Networking and Wireless.

---

