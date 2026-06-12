---
title: "Cant find built in wireless card?"
date: 2009-08-10
forum: Networking &amp; Wireless
---

### Post by Seathan93 on 2009-08-10
I'm trying to install ubuntu on my laptop (Gateway M series) and i followed the instructions to install ndiswrapper on ubuntu 9.04.  However now i cant find my wireless card, so i cant install the windows drivers using ndiswrapper.

Also when i type ndiswrapper -l it returns:

ls: cannot access /etc/ndiswrapper: No such file or directory

anybody got anything on this?  I had ubuntu working fine on my desktop at one point, and had no trouble installing ndiswrapper and the drivers, but my laptop is giving me trouble

**EDIT**

PROBLEM SOLVED STEPS BELOW

STEPS for M-6750 (though they're the same steps for most recent gateway models)

1.) Install ndiswrapper (sudo apt-get install ndisgtk)

2.) Download file at: [http://firmware.netgear-forum.com/WN511T/wn511t_3_0_setup.zip](http://firmware.netgear-forum.com/WN511T/wn511t_3_0_setup.zip) and then copy it to the /tmp folder

**Download it in Linux using a wired connection, it doesnt seem to work if you download it in windows, especially vista, though you might get it to work if you use XP

3.) unzip wn511t_3_0_setup.zip

4.) sudo apt-get install cabextract
5.) cabextract wn511t_3_0_setup.exe
6.) cd Disk1/

7.) sudo apt-get install wine
8.) wine ./Setup.exe

**Note, install with wine, keep going until it stops by itself (or crashes), that doesnt matter, you just need the files

9.) cd .wine/drive_c/Program\ Files/NETGEAR/WN511T/

10.)install using ndiswrapper:
a.) sudo ndiswrapper -i NetMW14x.inf
b.) sudo ndiswrapper -a 11ab:2a08 netmw14x  (apparently this forces the driver to use the wireless card)
c.) sudo ndiswrapper -m
d.) sudo depmod -a
e.) sudo modprobe ndiswrapper

And then apparently you're suppose to remove the .wine/ folder if it's the first time using wine (though i'm not sure why)

go (using the GUI i believe) to your home folder press Ctrl-H to show hidden folders, remove the .wine/ folder press Ctrl-H again

You may have problems getting the files, just make sure your repositories allow you to get the files off the Ubuntu disk and allow third party software

to do that go to System/Administration/Synaptic Package Manager
Settings/Repositories
then hit the "third party software" tab and check the two links

Thanks to the Ubuntu forums for the information and wstout and Iswb for their help

**EDIT 2**

Dont delete the .wine/ directory (or if you do, re-install the WN511T files) then, and you may not have to but i do so you might also, make the following script:

gksudo gedit /etc/init.d/wirelessfix.sh  (wirelessfix.sh can be changed to any name you want)

when the file pops up type in:

#!/bin/bash
cd .wine/drive_c/Program\ Files/NETGEAR/WN511T/
sudo ndiswrapper -i NetMW14x.inf
sudo ndiswrapper -a 11ab:2a08 netmw14x
sudo ndiswrapper -m
sudo depmod -a
sudo modprobe ndiswrapper

then save the file and go back into the terminal

cd /etc/init.d/

sudo chmod 755 wirelessfix.sh

sudo update-rc.d wirelessfix.sh defaults

you may not need to make this script, however i did because every time i re-started my computer wireless would stop working...this script makes ubuntu start up about 5 seconds slower and requires you to put in your keychain password (only slightly annoying) but it works

---

### Post by wstout on 2009-08-10
Go to Applications, Accessories, and open up the terminal. Type "lspci" without the quotes and copy and paste the output if you don't mind. I have a feeling there is a more "GUI" way of getting your card going.

---

### Post by Seathan93 on 2009-08-10
Output:
> 
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 2a08 (rev 03)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)

I think i might have found the drivers required (went to gateway's website) but i'm not quite sure, and i'm not sure what i'm looking for so any help is appreciated (also the driver i think i found is a .exe file and ndiswrapper told me i'm looking for a .zip flie)

---

### Post by wstout on 2009-08-10
What is the model number of the computer? I didn't see what i was expecting there, I'm not an expert but have had my fair share of wireless problems.

---

### Post by Seathan93 on 2009-08-10
It's a Gateway M-6750

the built in wireless card had a switch on the side (and an on/off key press) and yes they're both on, wireless works in windows

---

### Post by wstout on 2009-08-10
Ok this is probably over my head a little, have you tried going to system, administration, hardware drivers and seeing if there is an option to enable your driver from there? If so that's by far the easiest and best way in my opinion, if not here is a link to someone that got it going [http://ubuntuforums.org/showthread.php?t=1175864&page=2](http://ubuntuforums.org/showthread.php?t=1175864&page=2)  alot to read through but that user got things going with ndiswrapper

---

### Post by lswb on 2009-08-10
The Marvell device is the wireless adapter. Here's a guy who got it going with the same computer:

[http://www.joewein.net/blog/2008/03/10/first-impressions-of-vista-and-ubuntu/](http://www.joewein.net/blog/2008/03/10/first-impressions-of-vista-and-ubuntu/)

---

### Post by Seathan93 on 2009-08-10
Yeah i found that link while reading through the other link provided by wstout, i'll let you know if it works.

---

### Post by Seathan93 on 2009-08-10
ok so i know what driver i need (NetMW14x.inf and .sys) and i technically know where to get it, the only problem is, those drivers will only appear if you install them using XP, if you try with vista a different set of drivers pops up, on the website mentioned above he suggests using XP or even windows 2000 drivers, will vista drivers still work?

*EDIT*
Never Mind, there doesnt seem to be a .inf file with the vista drivers :\

---

### Post by wstout on 2009-08-10
Just out of curiosity did you try the hardware drivers from the system menu?

---

### Post by Seathan93 on 2009-08-10
yeah i did it said no proprietary drivers are in use on this system, and then had a blank box

---

### Post by Seathan93 on 2009-08-10
i'm not sure if this helps, but, you said the Marvel was the wireless network card, but on another thread they said realtek was their network card and i have both of something (though i'm not sure what) i did exactly what the guy did in the link and that didnt work so if this helps at all:

lspci -v output:

> 02:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 2a08 (rev 03)
	Subsystem: Marvell Technology Group Ltd. Device 2a08
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at f6000000 (32-bit, non-prefetchable) [size=64K]
	Memory at f4000000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>

06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
	Subsystem: Gateway 2000 Device 0380
	Flags: bus master, fast devsel, latency 0, IRQ 2299
	I/O ports at 4000 [size=256]
	Memory at fa200000 (64-bit, non-prefetchable) [size=4K]
	[virtual] Expansion ROM at c2000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169





---

### Post by Seathan93 on 2009-08-11
Solved the problem, will post instructions on first post

---

### Post by Seathan93 on 2009-08-12
*BUMPED* instructions now on first post

---

### Post by DiamondBuntu on 2010-02-23
I am riding the Ubuntu wave and lovin it!!!
Thanks for the detailed tutorial as I got mine working in the first shot.
Real life Saviour!!!

---

