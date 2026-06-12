---
title: "Wireless - Toshiba Satilite Pro L10"
date: 2010-06-23
forum: Networking &amp; Wireless
---

### Post by patferg on 2010-06-23
[B]Okay,

I am relativiely new to linux, but i've been trying to get this wireless up for a long time. I installed ndiswrapper and my wireless card. but anyway, i found this article that explains how to do it: 

[/B]

I feel like I’ve run the Comrades Marathon.

I recently installed Kubuntu Edgy on a friend’s machine. It’s an identical machine to mine – almost. Mine’s a Toshiba Satellite L10-101, her’s is a Toshiba Pro L10. I’ve already blogged about what I needed to do to get wireless working on my machine. Thankfully Feisty (which I checked out over the weekend) makes the great leap forward of actually including KNetWorkManager, so most people will be able to connect, even via WPA, without facing the Catch 22 situation of needing extra downloads.

But back to the Toshiba Pro. Everything worked fine. Except (there had to be an exception didn’t there) the wireless network card was not detected. Of course, once you know how, the 5 little commands seem entirely trivial, but it took me a good while to find out what to do!

This solution should work on any flavour of Linux requiring wireless connectivity. In my searches I saw zillions of forum posts about similar issues, with people using everything from Ubuntu, Kubuntu, Gentoo, SUSE, Red Hat and Fedora all getting stuck. The problem has nothing to do with Kubuntu, KNetworkManager, Wireless Assistant, NetworkManager or anything else beyond the basic level, so all my time spent looking there was a deadend.

Here’s what I needed to do:

1) Install the Windows wireless network driver from the Toshiba disk.
It’s probably something like:
sudo ndiswrapper -i /media/cdrom/Wireless\ Network\ Driver/Ambit/Winxp/neti2220.inf
or

sudo ndiswrapper -i /media/cdrom/Wireless\ Network\ Driver/Intel\ 802.11bg/w29n51.INF
If you do have to copy the files, make sure the .sys file is also present in the same directory. If you need to install ndiswrapper, it’s available from the Ubuntu respositories, and is probably also available on most other distros.

2) Check that it’s correctly installed.
sudo ndiswrapper -l
neti2220 : driver installed
device (17FE:2220:1468:0310) present
device (17FE:2220) present

w29n51 : driver installed

3) Create dependency file
sudo depmod -a

4) Load ndiswrapper module
sudo modprobe ndiswrapper

5) Load automatically on boot
$ sudo ndiswrapper -m

Thank you thank you thank you to user CalgaryStevens who saved the day on Kubuntuforums!

Not being native, it runs a little bit flakily, occasionally needing a reconnect to actually connect, but at least it works, and I haven’t unjustly put someone off Kubuntu for life!


[B]Okay,

so this is what happened: 
[/B]
laura@lauras:~$ sudo ndiswrapper -l
[sudo] password for laura: 
drivername : driver installed
w29n51 : driver installed
laura@lauras:~$ sudo depmod -a
laura@lauras:~$ sudo modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
laura@lauras:~$ 
[B]
I wonder if i installed the driver correctly, but it says it is installed when i try to do it again. I've also downloaded the driver from the website but still no luck.

any ideas?

thanks

[/B]

---

### Post by tkofford on 2012-01-19
I also have a toshiba laptop which uses the neti2220.inf driver. I am using Ubuntu desktop 32-bit version 11.10, and my laptop is a Toshiba Satellite L15-S104. 

I had given up on getting the internal wifi adapter to run under ubuntu (9.x, 10.x. 11.x) and have been using a wifi USB dongle for a long time. However, I decided to install the ndiswrapper package, and then subsequently installed the old eti2220.inf driver via ndiswrapper. I followed the instructions in [_WifiDocsDriverNdiswrapper_]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") exactly.

After it finished installing, it worked!!! However, when I restarted the system, my ndiswrapper driver would not load. I confirmed that it was present and installed, but when [FONT=Arial]I ran "sudo lshw -C network" [/FONT]the driver had a status of [FONT=Arial]UNCLAIMED[/FONT]. I removed and re-installed the driver again, and again it worked, so I ran "sudo lshw -C network" again and saw that the driver had a status of ENABLED. When I restarted my system though, I had the same problem as before, where the driver was not loaded. 

I've read through section "3.7. Automatically loading at start-up" in the [WifiDocsDriverNdiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") docs, and followed all the directions each time, but this problem still persists. For some reason, the wifi driver will not load during startup.

Any suggestions? I'd hate to go back to using the dongle if I know there's a possibility the ndis driver will work.

Thanks in advance,

TK

---

### Post by tkofford on 2012-01-23
OK, solved my problem.

Open a terminal and issue the following commands:
[I]         sudo ndiswrapper -m
         gksudo gedit /etc/modules    [/I]
and add the following module to the list          "***ndiswrapper***" w/out quotes.

Note having the "ndiswrapper" entry in the /etc/modules file was the problem.

Hope this info can help someone else!

-TK

---

