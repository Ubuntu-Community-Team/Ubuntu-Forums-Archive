---
title: "hp pavilion dv3 atheros 802.11 problem"
date: 2009-02-17
forum: Networking &amp; Wireless
---

### Post by cecilmoney on 2009-02-17
I just got a brand new hp pavilion dv3. It has the atheros 802.11 wlan card. ubuntu has a driver installed that supposedly supports this card. 

The problem is, my wifi touch button is indicating that my wireless is turned off. 

I cannot turn on the wireless via the touch button. No wifi connections appear when I click on the network manager.

in my attempt to fix the problem, I downloaded and installed the modwifi packages, which provided me with a new wlan driver. This did not fix my problem at all. 

I have no idea how to use "modwifi", so I would guess that I'm probably not using it right.

I have absolute no idea what to do; please help me!

---

### Post by superprash2003 on 2009-02-17
please post output of the following commands from the terminal
1)lshw -C network
2)iwlist scanning
3)iwconfig

---

### Post by cecilmoney on 2009-02-17
1. 
dave@dave-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:ec:fc:66:27
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.6 latency=0 module=r8169 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 6a:fe:eb:7f:37:13
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


2.
dave@dave-laptop:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.



3.
dave@dave-laptop:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

dave@dave-laptop:~$ 
dave@dave-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.



I currently have the default drivers turned off and the madwifi 5xxx series driver turned on. I'll swap the drivers, reboot, and post the results of those inputs again.

---

### Post by 5BallJuggler on 2009-02-17
Try this:

[http://ubuntuforums.org/showthread.php?t=1054629](http://ubuntuforums.org/showthread.php?t=1054629)

---

### Post by cecilmoney on 2009-02-17
With the default atheros 802.11 driver activated:

1.
dave@dave-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:ec:fc:66:27
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.6 latency=0 module=r8169 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: ce:80:19:20:43:49
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


2.
dave@dave-laptop:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.



3.
dave@dave-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.



There you go. I think that the problem might be that I can't use my touch button to toggle wifi on and off. It's glowing red, indicating that wifi is off. 

I really don't know.

---

### Post by Ketara on 2009-02-17
How brand new is this computer?

Did the wireless work in windows before you installed Ubuntu?

Maybe it's just me, but I think the wireless card on-off switch should be working regardless of whether or not you have a working driver. It should turn "on" (blue light) and then just not work anyway, which makes me think there's another problem here.

---

### Post by cecilmoney on 2009-02-17
I followed that walkthrough to a T, and it didn't help.


The hp pavilion dv3 is brand new. I ordered it on the first day it came out.

I have a 64 bit version of vista dual booted and the wireless works fine. All of my other touch buttons appear to function in ubuntu. 

Is there any other information I could provide?

---

### Post by cecilmoney on 2009-02-17
WOAH!

I just rebooted with my atheros 5xxx driver activated and my default driver off, and now I can recognize wifi signals!

However, I still can't connect to any of them. only the first of the two green lights lights up when I attempt to connect to a wireless network. 

I feel like we are making some progress. 

My wifi light is still solid red.

---

### Post by Ketara on 2009-02-17
I guess that means it's okay to ignore the light.

Are the networks you're attempting to connect to secured or unsecured?

I had that exact problem for a while on Hardy with this card, where I couldn't connect to any networks but I could see them fine.

---

### Post by cecilmoney on 2009-02-17
I'm attempting to connect to a secured network. It prompted me for the password (which I put in) and then just sat there on the first green light until it prompted me for the password again.

---

### Post by Ketara on 2009-02-17
See if you can get onto an unsecured network, so we know whether or not the driver is working properly.

You can also try a different network manager. When I had that problem before the card wouldn't connect to secured networks under network-manager but it would with Wicd. You will have to add wicd to your Synaptic repository to download it, but the instructions are pretty simple: 

[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

If for some reason that makes the issue worse, re-installing network-manager via synaptic is easy to do.

---

### Post by 5BallJuggler on 2009-02-17
If your network is secured, you may need to put your router into pairing mode.

---

### Post by cecilmoney on 2009-02-17
I used "apt-get install" to get wicd and I added the sources and now my wifi works perfectly. 

Thanks all for the help!

---

### Post by cecilmoney on 2009-02-18
I decided to re-install ubuntu to expand my linux partition. 

I figured that if this stuff worked the first time, that I should just be able to do it again and everything should work out the same way.

So I re-installed, followed the walkthrough to install my ath5k driver, added the wicd sources, and downloaded wicd; except now, my wireless doesn't even pick up a signal. 

when I do this:


sudo lshw -C network

I get this:

dave@dave-laptop:~$ sudo lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wmaster0
       version: 01
       serial: 00:24:2b:56:55:77
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:ec:fc:66:27
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.6 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 12:91:e3:a6:74:a7
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


did I forget to do something?

---

### Post by Ketara on 2009-02-18
Check to see if you have ath5k blacklisted somewhere. Open in terminal:

gksudo gedit /etc/modprobe.d/blacklist

and then see if ath5k is anywhere in that file. If it is, comment it by adding a # sign in front of it, so it will look like:

"# blacklist ath5k"

(note: Any time you edit a file with root priveleges be extremely careful, as accidents can cause serious system damage)

If that doesn't work, is it possible you installed a different linux kernel? Was your previous install not fully updated?

---

### Post by Snypercell on 2009-02-18
> **Ketara said:**
> How brand new is this computer?

Did the wireless work in windows before you installed Ubuntu?

Maybe it's just me, but I think the wireless card on-off switch should be working regardless of whether or not you have a working driver. It should turn "on" (blue light) and then just not work anyway, which makes me think there's another problem here.


i'm having the same issues with an Atheron AR242x. my light will not turn blue ethier.

---

### Post by Snypercell on 2009-02-18
i'm in the same boat as the first guy, but i have a question. how do i install atheros 5xxx from another machine, since i cant get this one online atm?

---

### Post by Ketara on 2009-02-18
Snyper,

What have you tried to fix it? It is difficult to be of help if we don't know what has/has not worked so far.

Are you running Hardy or Intrepid?

---

### Post by Snypercell on 2009-02-18
and how do i update my kernal from a fresh intall?

---

### Post by Snypercell on 2009-02-18
Hi Ketara and thnx,
 you see, i dont really know anything about linux. i'm good w/ a pc, but this is all alen to me lol. not really all, but most.
i dont even know the difference, in short, lol

---

### Post by Ketara on 2009-02-18
I replied on the thread you made.

---

### Post by Snypercell on 2009-02-18
i havent really tried anything. i installed Ubuntu 8.04.2 64Bit onto my laptop (hpdv6700), which i downloaded from the website. 
when the install finished it stated that my HAL and Atheron drivers were good, and that the nvidia needed updated. 
 nothing even shows up as far as wifi. 
 i disabled the Atheron and blaklisted it.
 now i just need to install a new driver, i assume, but i cant get said machine online, so i'm having to downlad with another pc, and file tranfer. 
 i need to know how to install this way.

---

### Post by cecilmoney on 2009-02-18
I opened that list of blacklisted drivers and ath5k was not on there.

---

### Post by cecilmoney on 2009-02-18
Also, I booted 2.6.27-12-generic with both installs.

---

### Post by cecilmoney on 2009-02-18
nothing I try seems to be working... Should I try to re-install or something?

---

### Post by Ketara on 2009-02-19
No, it's very unlikely (and a pain to do) that reinstalling will help. It's much more likely that you missed a step somewhere, or did something extra the first time around that you forgot.

Lets see if we can figure it out. I shall make a checklist for you.

#1 - Is the wireless card turned on via the keyboard switch?

#2 - Is the driver in hardware devices set to ath5k?

#3 - Check blacklist. ath_hal and ath_pci should be blacklisted. If not, blacklist them.

#4 - Make sure ath5k and ath9k are not blacklisted.

#5 - Try it with both Wicd and network-manager

#6 - Try reinstalling backports and ath5k via that thread. It's possible you missed a step or had a freak corrupted install.

If none of that seems to be getting it working, we can see if ndiswrapper will get it to work.

---

### Post by cecilmoney on 2009-02-19
My problem was that I didn't have "wlan0" typed in the first box of the wicd preferences. 

super lame. 

Wifi works fine now.

---

