---
title: "Ubuntu server doesn't find my other network devices"
date: 2010-06-30
forum: Networking &amp; Wireless
---

### Post by TheAlien on 2010-06-30
I've got three network devices on a laptop:
 
1. Built-in ethernet LAN
2. Built-in ethernet WLAN
3. PCMCIA ethernet LAN
 
I installed Ubuntu Server on this computer without the last one inserted.
 
I inserted the last one today, and it lights up when i put in the cable. To be sure if Ubuntu has found it, I tested with the install CD and could see that it found all three at the first part of the installation where I have to chose a primary device.
 
But inside Ubuntu, it only finds the first device: eth0.
 
I've tried
```
 
ifconfig -a

```
but it finds only eth0
 
I've tried:
```
 
sudo ifconfig eth1 up
sudo ifconfig eth2 up
sudo ifconfig eth3 up

```
I only get errors about unknown device
 
I've tried:
```
 
lspci

```
But only find one line with the name Ethernet, and that's eth0 that works.
 
I can't get my WLAN card working, neither do I get my PCMCIA LAN card working. The third card, this PCMCIA card, has worked on Ubuntu Desktop using another laptop. And as said, the setup finds all three.
 
I'm so confused now. Does anyone have any clue about what to do now?
Please be aware that I'm using Ubuntu Server with no GUI, so I can't copy/paste.
 
Thanks in advance! :)

---

### Post by Iowan on 2010-06-30
Probably the same information in a different format, but what does **sudo lshw -C network** show?

---

### Post by TheAlien on 2010-07-01
> **Iowan said:**
> Probably the same information in a different format, but what does **sudo lshw -C network** show?
 
It says: ***-network, configuration:, resources:,** with info about what seems to only be my eth0 card.
 
But's thats all. :/
 
It seems like the WLAN and PCMCIA card doesn't exist in Ubuntu Server, even though they all appears when I install it and using the install CD and have to chose a prirmary network device. :/

---

### Post by TheAlien on 2010-07-01
Hm, this is very strange!
 
I tried to re-install Ubuntu Server to see if I needed the install CD to get the correct drivers for the PCMCIA card that doesn't work on Ubuntu Server when I plug it in.
 
As I've written, the installer finds it at the beginning of the install process. So this time I chose this PCMCIA as the primary network interface during install to see what happened.
 
Strange as it is, it works during the install! I mean, it updates the time over internet and finds my time zone, and it even does a search over the internet during the apt part of the installation! I see the led on the device flash during data transfer!
 
BUT when the installation is done, and I'm booting into Ubuntu Server, the device is gone from the system, except for /etc/network/interfaces where it's listed, and the only remaining Ethernet device when entering ifconfig -a is the internal Intel network device that always works.
 
Does anyone even know what this can be? This is a really strange problem! It works during install, but not when I'm logged into the system after the install!

---

### Post by TheAlien on 2010-07-01
The Ubuntu forum didn't bump my post after I replied, so I've have to add this link to the thread, because i really need help and I don't want the thread to get burried:
 
 
Thanks!

---

### Post by TheAlien on 2010-07-01
I tried installing Ubuntu Desktop on the laptop, and both LAN cards works flawlessly!
 
But I want to use Ubuntu Server, so I still want help for this. Thanks! :)

---

### Post by Iowan on 2010-07-01
Threads merged.

---

### Post by TheAlien on 2010-07-03
No one knows how to solve this?
 
(asking for the last time)

---

### Post by Iowan on 2010-07-03
I know there are some differences between the desktop and server kernel, and what drivers each support, but I'm not sure if wireless is one of those features the server omits...

---

### Post by TheAlien on 2010-07-03
> **Iowan said:**
> I know there are some differences between the desktop and server kernel, and what drivers each support, but I'm not sure if wireless is one of those features the server omits...

The wireless card isn't that important. I only need the two LAN devices. One is built in and one is external.

What I don't get is that the external (problem) card works during the install, but not when you log into Ubuntu Server. It even goes online during the bootup before login, so when I log in to the server, it tells me that so and so many packages can be downloaded, and etc. But in the moment I log in, the card is gone from the system. It's super weird!

It might be as you say, that the server edition doesn't support that external card. I don't want to offend anyone, but that's _really_ weak of Ubuntu Server! It should have at least as good network device support as the desktop edition, or even better support. Server + Network devices = Very important.

---

### Post by penquissciguy on 2010-07-30
I'm having the same exact issue.  My orinoco pcmcia wireless card is supported no problem during the install, but is nowhere to be found after the install finishes and I boot up my machine.  Using modprobe to insert modules and adding modules to the /etc/modules list makes no difference.  An answer to what is happening here would be greatly appreciated.  

> **TheAlien said:**
> The wireless card isn't that important. I only need the two LAN devices. One is built in and one is external.

What I don't get is that the external (problem) card works during the install, but not when you log into Ubuntu Server. It even goes online during the bootup before login, so when I log in to the server, it tells me that so and so many packages can be downloaded, and etc. But in the moment I log in, the card is gone from the system. It's super weird!

It might be as you say, that the server edition doesn't support that external card. I don't want to offend anyone, but that's _really_ weak of Ubuntu Server! It should have at least as good network device support as the desktop edition, or even better support. Server + Network devices = Very important.

---

