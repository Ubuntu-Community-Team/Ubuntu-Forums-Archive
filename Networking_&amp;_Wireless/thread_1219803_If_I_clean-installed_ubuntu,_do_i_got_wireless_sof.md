---
title: "If I clean-installed ubuntu, do i got wireless soft?"
date: 2009-07-22
forum: Networking &amp; Wireless
---

### Post by gregapan on 2009-07-22
I finally went ubuntu, and did it whole-hog, wiping off a buggy old XP from my hd. This laptop has wireless hardware, but any software that came with the original is long gone. Was I a fool to do it this way? At the moment, I can't seem to find any way to connect to my home network. (I have a Belkin router that is working fine with two other non-linux machines.) I have entered the necessary info in the Network Connections. 
Do I need to obtain some software elsewhere and install it with a usb memory stick?
Pardon the newbie-ness.
Please advise.

---

### Post by t0mppa on 2009-07-22
> **gregapan said:**
> I finally went ubuntu, and did it whole-hog, wiping off a buggy old XP from my hd. This laptop has wireless hardware, but any software that came with the original is long gone. Was I a fool to do it this way?

No, not a fool. Hardware manufacturers tend to take the easy way out and simply write software to handle their hardware on one OS, where the defacto standard unfortunately is Windows nowadays. And any software written for Windows won't run on Linux without some tricks, so it's easier to just switch to new software that's written for Linux.

> **gregapan said:**
> At the moment, I can't seem to find any way to connect to my home network. (I have a Belkin router that is working fine with two other non-linux machines.) I have entered the necessary info in the Network Connections.
Do I need to obtain some software elsewhere and install it with a usb memory stick?
Pardon the newbie-ness.
Please advise. 

Can you see your network, or any network for that matter, when clicking on the Network Manager icon (see the screenshot)? If it's all greyed up, then your wireless isn't working properly yet and you need to do some troubleshooting. For that to happen, open up a terminal (Applications / Accessories / Terminal), run **lshw -C network** and post back with the results. That will show the current state of the card and what, if any, drivers are associated with it.

---

### Post by gregapan on 2009-07-22
Hi, me again.
Thank you for your support so far.
You asked me to run the command and post the results.
I am pasting them here. Hope you can tell me what these tea leaves augur...

To run a command as administrator (user "root"), use "sudo <command>". 
See "man sudo_root" for details. 
 
greg@greg-laptop:~$ lshw-C network 
bash: lshw-C: command not found 
greg@greg-laptop:~$ Ishw-C network 
bash: Ishw-C: command not found 
greg@greg-laptop:~$ lshw -C network 
WARNING: you should run this program as super-user. 
  *-network:0              
       description: Ethernet interface 
       product: RTL-8139/8139C/8139C+ 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: c 
       bus info: pci@0000:01:0c.0 
       logical name: eth0 
       version: 10 
       serial: 00:0b:5d:4c:e3:3f 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes 
  *-network:1 
       description: Network controller 
       product: BCM4306 802.11b/g Wireless LAN Controller 
       vendor: Broadcom Corporation 
       physical id: d 
       bus info: pci@0000:01:0d.0 
       version: 02 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list 
       configuration: driver=b43-pci-bridge latency=64 module=ssb 
  *-network:0 DISABLED 
       description: Wireless interface 
       physical id: 2 
       logical name: wlan0 
       serial: 00:90:96:8a:45:49 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg 
  *-network:1 DISABLED 
       description: Ethernet interface 
       physical id: 3 
       logical name: pan0 
       serial: 6e:48:b1:40:4a:9c 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes 
greg@greg-laptop:~$

---

### Post by gregapan on 2009-07-22
ps
just to confirm, yes, the wireless bars are greyed out, with a nice fat red X, to boot.

---

### Post by Srvrdown on 2009-07-22
Im kind of having the same problem, however instead of a clean instal i did a dual boot with Vista Ultimate and Ubuntu 9.04, no matter what i do i cannot get my wireless card to connect, ive tried loading the windows .inf files, but im not sure if i even have the right one, my wireless card is a Dynex DX-WGPDTC and the .inf i got for it was bcmw15.inf and i also tried bcmw15a.inf.

When i resart and boot Vista i get connection instantly, but nothing with Ubuntu, i ran the lshw -c network here are the results

   [FONT=Verdana][SIZE=1]srvrdown@Thelma:~$ lshw -c network[/SIZE][/FONT]
  [FONT=Verdana][SIZE=1]WARNING: you should run this program as super-user.[/SIZE][/FONT]
  [FONT=Verdana][SIZE=1]  *-network               [/SIZE][/FONT]
  [FONT=Verdana][SIZE=1]       description: Network controller[/SIZE][/FONT]
  [FONT=Verdana][SIZE=1]       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller[/SIZE][/FONT]
  [FONT=Verdana][SIZE=1]       vendor: Broadcom Corporation[/SIZE][/FONT]
  [FONT=Verdana][SIZE=1]       physical id: 6[/SIZE][/FONT]
  [FONT=Verdana][SIZE=1]       bus info: pci@0000:01:06.0[/SIZE][/FONT]
  [FONT=Verdana][SIZE=1]       version: 02[/SIZE][/FONT]
  [FONT=Verdana][SIZE=1]       width: 32 bits[/SIZE][/FONT]
  [FONT=Verdana][SIZE=1]       clock: 33MHz[/SIZE][/FONT]
  [FONT=Verdana][SIZE=1]       capabilities: bus_master[/SIZE][/FONT]
  [FONT=Verdana][SIZE=1]       configuration: driver=b43-pci-bridge latency=32 module=ssb[/SIZE][/FONT]
  [FONT=Verdana][SIZE=1]  *-network DISABLED[/SIZE][/FONT]
  [FONT=Verdana][SIZE=1]       description: Ethernet interface[/SIZE][/FONT]
  [FONT=Verdana][SIZE=1]       physical id: 1[/SIZE][/FONT]
  [FONT=Verdana][SIZE=1]       logical name: pan0[/SIZE][/FONT]
  [FONT=Verdana][SIZE=1]       serial: ca:6b:33:3e:96:89[/SIZE][/FONT]
  [FONT=Verdana][SIZE=1]       capabilities: ethernet physical[/SIZE][/FONT]
  [FONT=Verdana][SIZE=1]       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes[/SIZE][/FONT]
  [FONT=Verdana][SIZE=1]srvrdown@Thelma:~$[/SIZE][/FONT]
[FONT=Verdana][SIZE=1]
[/SIZE][/FONT]
[FONT=Verdana][SIZE=1]i also blacklisted the other drivers that came with Ubuntu using code i found on another (long abandoned) forum "echo -e "blacklist bcm43xx\nblacklist b43\nblacklist b43legacy\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist"
[/SIZE][/FONT]
[FONT=Verdana][SIZE=1]
[/SIZE][/FONT]
[FONT=Verdana][SIZE=1]i uninstaled the windows infs and tried to use hardware detector (i think thats what it was) to re enable the blacklisted drivers but now under wireless connection it says "device not managed"[/SIZE][/FONT]
[FONT=Verdana][SIZE=1]
[/SIZE][/FONT]
[FONT=Verdana][SIZE=1]Please help me, im new to linux and was drawn in by open source and freedom, i know if i can get past this one little hurtle i will be on my way to enjoying pounding a keyboard again. 
[/SIZE][/FONT]


[FONT=Verdana][SIZE=1]Thanx in advance for your help!
[/SIZE][/FONT]

---

### Post by martinbaselier on 2009-07-22
@svrdown. Please read this post, it provides a workaround for your card. 

[http://ubuntuforums.org/showthread.php?t=1176117](http://ubuntuforums.org/showthread.php?t=1176117)

---

### Post by Srvrdown on 2009-07-22
wow thank you very much , navigating these forums can get daunting, i appriciate a nudge in the right direction

---

### Post by t0mppa on 2009-07-23
> **gregapan said:**
> Hi, me again.
Thank you for your support so far.
You asked me to run the command and post the results.
I am pasting them here. Hope you can tell me what these tea leaves augur...

greg@greg-laptop:~$ lshw -C network 
WARNING: you should run this program as super-user. 
  *-network:1 
       description: Network controller 
       product: BCM4306 802.11b/g Wireless LAN Controller 
       vendor: Broadcom Corporation 
       physical id: d 
       bus info: pci@0000:01:0d.0 
       version: 02 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list 
       configuration: driver=b43-pci-bridge latency=64 module=ssb 
  *-network:0 DISABLED 
       description: Wireless interface 
       physical id: 2 
       logical name: wlan0 
       serial: 00:90:96:8a:45:49 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg 


Ok, the interface being disabled is something that has to be fixed, however it could just be a byproduct of other issues. Since you probably haven't got the firmware required by b43, give the instructions [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx") a shot and see if it's as simple as that to fix.

---

### Post by gregapan on 2009-07-28
t0mmpa, thanks again.
If you're still out there, I am stuck on trying to install the drivers (that I downloaded to my usb flash by using a different, Windows machine) on ubuntu. How do I do this? I extracted the files for one of them, but that does nothing, of course.
This page ([https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)) says to "Execute the following necessary commands on the files above manually". I have no idea how to do that.

---

### Post by t0mppa on 2009-07-28
It simply means opening up a terminal and navigating to the directory where you extracted those files to and then running the commands, there's 3 of them with each on its own line and last one on two lines.

---

### Post by gregapan on 2009-07-28
Okay, but how does one "navigate" using a terminal? 
(If there is a tutorial about this online, let me know.)

PS
Is Ubuntu always this convoluted and not quite user-friendly, or is it just because I'm trying to access deeply embedded stuff? 
With Windows, running system command prompts was a rare necessity.

---

### Post by gregapan on 2009-07-28
.

---

### Post by t0mppa on 2009-07-29
> Okay, but how does one "navigate" using a terminal?
(If there is a tutorial about this online, let me know.)

Just like one would navigate on a command prompt on Windows: with *cd* commands. You'd find a zillion hits just by bothering to google about it. ;) [Here]("http://ubuntuforums.org/showthread.php?t=73885")'s a thread on these forums about the terminal commands.

> PS
Is Ubuntu always this convoluted and not quite user-friendly, or is it just because I'm trying to access deeply embedded stuff?
With Windows, running system command prompts was a rare necessity. 

Just like with Windows, there's usually a GUI available for most things, if you don't like typing commands. For instance, in your case, like the wiki page says, the same thing could be accomplished simply by connecting to Internet through alternative means. wired interface for example, and then using the Hardware Drivers GUI under System and Administration.

Working through terminal just usually gives you more options and lets you better specify what you want to do.

---

