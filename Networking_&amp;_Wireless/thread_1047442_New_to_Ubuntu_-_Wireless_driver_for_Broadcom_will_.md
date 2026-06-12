---
title: "New to Ubuntu - Wireless driver for Broadcom will not enable"
date: 2009-01-22
forum: Networking &amp; Wireless
---

### Post by EvilBear on 2009-01-22
Hi, I've only been using Ubuntu for half a year now, as my programmer friends said if i wanted to start programing Linux would be a great OS. My wireless has always been fine, but after updating my computer my Broadcom driver stopped working. I have classes starting next week and need wireless. Anyone able to help? Dell support says i need to reinstall and lose all my music/movies/etc unless i can figure out how to back up 200 gigs of stuff.

Info for Wireless

id:	
network
description: 	Wireless interface
product: 	BCM4312 802.11b/g
vendor: 	Broadcom Corporation
physical id: 	
0
bus info: 	
pci@0000:0c:00.0
logical name: 	
eth1
version: 	01
serial: 	00:1f:e1:a0:fd:0b
width: 	64 bits
clock: 	33MHz
capabilities: 	pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration:	
broadcast	=	yes
driver	=	wl
ip	=	172.30.1.57
latency	=	0
module	=	wl
multicast	=	yes
wireless	=	IEEE 802.11bg

I don't understand any of that, but someone here might.

When i go to enable driver it gives me the restart symbol but doesn't enable it.

TY for any help.

Adam

P.S. My landline works fine so i have internet at home, just no wireless.

---

### Post by Old *ix Geek on 2009-01-22
What version of Ubuntu are you using? And when you say "When i go to enable driver it gives me the restart symbol but doesn't enable it," WHERE are you doing this?

I just installed Intrepid on my HP dv6000 laptop, which has the Broadcom 43xx card, and had no problems.  I used a wired connection during the install and when it got to detecting the Broadcom card, it offered to download and activate the appropriate drivers; I selected that option and everything proceeded without a hitch.  Have you tried using a wired connection to activate the card?

---

### Post by EvilBear on 2009-01-22
I am running Hardy Heron and have installed all the updates.

By enabling, i mean I select System, then Administration, the Hardware drivers. It shows the device driver for Broadcom STA Wireless Driver not enabled(status:not in use). I click the box that says enable, nothing changes, but in the upper right hand corner a symbol appears next to my Batterey symbol to restart my laptop before changes will take place. Restarting changes nothing. Also, I am using Gnome if that helps at all but know a little about the CLI.

---

### Post by EvilBear on 2009-01-22
As for wired connection to activate the card, no idea at all how to do that. I do have a wired connection, but enabling a driver is a mystery to me.

---

### Post by EvilBear on 2009-01-22
Ok, i will assume that the lack of replies means that its a hard question. Is there anywhere else i can go for info please? Need this up and running by monday for my C++ and other computer classes.

---

### Post by Ayuthia on 2009-01-22
Can you post the results of lspci -nn and also let us know if you are using WEP or WPA?  I am guessing that you have a 14e4:4315 chipset, but I need to confirm.  The wl module does not like WPA/WEP too much so I just want to confirm this also.

All of these commands need to be run in the Terminal.

---

### Post by EvilBear on 2009-01-22
ok, when i type the lspci -nn this came up. Too green to know what WEP or WPA are, sorry.
If you tell me what to put at the CLI i can do that though. Know that much. TY

 lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 03)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 03)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
03:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
03:01.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
03:01.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe [14e4:1698] (rev 10)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)

---

### Post by Ayuthia on 2009-01-22
Let's see if you can scan for any wireless sites:
```
sudo iwlist scan
```This will help us see if your router is encrypted or not.

It might also be possible that you might need to download the newer release of the [Broadcom STA module]("http://www.broadcom.com/support/802.11/linux_sta.php").

It looks like they have released something as of the 21st of January so I have not had a chance to test it out yet.  Their previous release seemed to work better with encrypted networks.

---

### Post by EvilBear on 2009-01-23
Sorry, i had to go to work.

OK, i did the scan and got this:


lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Failed to read scan data : Invalid argument

No idea what that implies, but there it is. I'll try the new driver in a bit as well.

Edit- Ok, just went to the link you provided and was all kinds of newb confused. No idea how to check the 32 or 64 bit thing, etc. I remember a little bit about tar's. I can use a book for that prolly. Sorry to bug you, but can you walk me through that link you provided?

---

### Post by Ayuthia on 2009-01-23
If you go into the Terminal you can use uname -m and it will tell you if you have a 64-bit (x86_64) or a 32-bit (i-x86).

You can also try this [link]("http://linuxfans.betaserver.org/index.php?option=com_content&view=article&id=48:guide-to-compiling-and-using-the-broadcom-sta-module&catid=34:guides&Itemid=61").  It is a guide on how to install the module.  You should not need to apply the patch because I think that their newer releases are set for the newer kernels.

---

### Post by Old *ix Geek on 2009-01-23
> **EvilBear said:**
> I am running Hardy Heron and have installed all the updates.

By enabling, i mean I select System, then Administration, the Hardware drivers. It shows the device driver for Broadcom STA Wireless Driver not enabled(status:not in use). I click the box that says enable, nothing changes, but in the upper right hand corner a symbol appears next to my Batterey symbol to restart my laptop before changes will take place. Restarting changes nothing. Also, I am using Gnome if that helps at all but know a little about the CLI.

Do you have access to a cable to physically connect your laptop to your DSL box or router?  I don't use Gnome so I'm not at all familiar with the symbols you're describing, but it SOUNDS to me like you just need a connection so you can download and then activate new drivers.  Since you're not connected, your attempts to activate aren't working because the computer's trying to download the drivers but can't.  This is just a guess, but worth a try.

---

### Post by EvilBear on 2009-01-23
ok, 32 bit it is.

evilbear@dell-desktop:~$ uname -m
i686

---

### Post by EvilBear on 2009-01-23
> **Old *ix Geek said:**
> Do you have access to a cable to physically connect your laptop to your DSL box or router?  I don't use Gnome so I'm not at all familiar with the symbols you're describing, but it SOUNDS to me like you just need a connection so you can download and then activate new drivers.  Since you're not connected, your attempts to activate aren't working because the computer's trying to download the drivers but can't.  This is just a guess, but worth a try.

Yes, that is how I am accessing the internet currently. The upgrades to Hardy are what disabled and caused the problems with my wireless. I will try the new module that just came out and see if it works. If that doesn't work and you have any ideas, i can work from the CLI if given instructions as well. TY.

---

### Post by Ayuthia on 2009-01-23
> **EvilBear said:**
> Yes, that is how I am accessing the internet currently. The upgrades to Hardy are what disabled and caused the problems with my wireless. I will try the new module that just came out and see if it works. If that doesn't work and you have any ideas, i can work from the CLI if given instructions as well. TY.
You might try going back to the previous kernel to see if it works.  When you start up, there should be a menu that pops up that lets you select a kernel version.  If it does not, then you should be able to press escape and then go back to the previous version.

It could also be possible that Network Manager might be the problem also.  If you are able to go back to a previous version and it does not work, then it most likely is Network Manager.

---

### Post by EvilBear on 2009-01-23
Ok, followed the guide to install and everything seemed to go smooth, but after rebooting it still doesn't work. Will try it again and test it to see if it works before rebooting.

Also, the .txt that is on the module page has this at the end-

[I]"Some kernel come with pre-installed Broadcom driver that support Broadcom 4312 family of
PCIE cards. If the kernel support one of those pre-installed driver, you must remove it
in order to install the new driver.  Some of existing driver provided by the Linux community that
supports Broadcom hardware are b43/b43legacy/bcm43xx.  There is also a ssb driver that is loaded
along with b43. This ssb driver also must to be remove.

If the kernel supports blacklist, you can add those drivers to the blacklist file so that it will
not be loaded on next reboot."[/I]

Don't know if that may have something to do with it. Don't know how to remove or blacklist things.

The .txt file instructions also say-

[I]4.  Cleanup (optional):                  make -C /lib/modules/<2.6.xx.xx>/build M=`pwd` clean
5.  Build the LKM, i.e. wl.ko:           make -C /lib/modules/<2.6.xx.xx>/build M=`pwd`[/I]

when i list that directory, there are 

drwxr-xr-x 9 root root 4096 2008-09-26 14:26 2.6.24-16-generic
drwxr-xr-x 8 root root 4096 2008-09-26 14:29 2.6.24-19-generic
drwxr-xr-x 8 root root 4096 2008-11-21 14:22 2.6.24-21-generic
drwxr-xr-x 8 root root 4096 2008-12-03 11:39 2.6.24-22-generic
drwxr-xr-x 8 root root 4096 2009-01-22 07:42 2.6.24-23-generic

am i supposed to do those instuctions for all of these or just certain ones? Don't wanna accidently mess something up i don't fully understand.

I will follow the guide again and see if it works before rebooting.

---

### Post by EvilBear on 2009-01-23
OK, that didn't work. But I rebooted and saw the different kernel options. is there a specific one that should work or should I just keep trying them one at a time from newest to oldest(which is what i'll try until told otherwise). Hopefully that'll do it.

---

### Post by EvilBear on 2009-01-23
Went to the oldest option, ending in .16, still will not allow the wireless driver to enable, will not connect.

---

### Post by EvilBear on 2009-01-23
> **Ayuthia said:**
> You might try going back to the previous kernel to see if it works.  When you start up, there should be a menu that pops up that lets you select a kernel version.  If it does not, then you should be able to press escape and then go back to the previous version.

It could also be possible that Network Manager might be the problem also.  If you are able to go back to a previous version and it does not work, then it most likely is Network Manager.

So, how do i try out that Network Manager possibility?

---

### Post by Ayuthia on 2009-01-23
If you do:
```
ps -ef|grep Network
```
You should see a couple of entries for Network Manager.  You will need to kill those processes (Don't worry.  If you kill the process and it does not work, you can reboot and things will be back to where you started.).  For example:
```
auser   5159  5092  0 Jan22 tty1     00:00:02 xterm -bg black -fg white
auser   5344  5092  0 Jan22 tty1     00:00:06 xterm -bg black -fg white
auser  24457 21371  0 12:11 pts/3    00:00:00 grep --colour=auto xterm

```You will see that there are two xterm sessions running.  To kill them, you will need to grab the process id of the two sessions.  In this case they are 5159 and 5344 (they are the first set of numbers for each process):
```
sudo kill 5159 5344
```
Once you have killed those processes, you can then try to see if you can scan with eth1:
```
sudo iwlist scan
```

Just let us know if you can see any wireless sites or not.  Of course, since you killed Network Manager, you won't be able to connect using the GUI methods.  If you lost your wired connection, you can connect again by using:
```
sudo dhclient eth0
```

If you are able to see wireless sites, then it most likely is Network Manager that is causing the problem.  You can then switch over to something else like wicd.  I just recommend trying this out before installing another package since it does not hurt anything.

---

### Post by EvilBear on 2009-01-23
Still nothing after killing those.

---

### Post by Ayuthia on 2009-01-23
If you are not opposed to using NDISwrapper, here is a guide on how to install it:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

It looks like you will need the driver in Step 2e.  The unpruned version is:
[ftp://ftp.us.dell.com/network/R174291.exe](ftp://ftp.us.dell.com/network/R174291.exe)

Just for reference, the page refers to the 4310 card instead of the 4312.  It really is the 4312 card, but was mislabeled in earlier versions.

The guide mentions that it is for Feisty, but it is up to date and has been working for Intrepid.

---

