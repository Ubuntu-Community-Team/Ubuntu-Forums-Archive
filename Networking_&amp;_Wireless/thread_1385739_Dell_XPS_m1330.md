---
title: "Dell XPS m1330"
date: 2010-01-19
forum: Networking &amp; Wireless
---

### Post by Sephenon on 2010-01-19
Ok I can't get my stinking dell m1330 to wirelessly connect with ANY networks I present it with.  Including PittNet (The University of Pittsburgh's wireless network), my home network which isn't even protected and Panera bread's public connection.  Anyone have ANYWHERE for me to start from?

---

### Post by rossmoore on 2010-01-19
OK, I've got a Dell XPS M1530 and (unhelpfully) it just works. To get some help, let's get some more details:
What version of Ubuntu are you using?
What's the output of "lshw -C network" in a terminal?
[Dumb question] - are you sure you haven't accidentally switched the wireless switch on the side of the laptop?!
Do you have NetworkManager in the notification area of your task bar?

---

### Post by Sephenon on 2010-01-20
> **rossmoore said:**
> OK, I've got a Dell XPS M1530 and (unhelpfully) it just works. To get some help, let's get some more details:
What version of Ubuntu are you using?
What's the output of "lshw -C network" in a terminal?
[Dumb question] - are you sure you haven't accidentally switched the wireless switch on the side of the laptop?!
Do you have NetworkManager in the notification area of your task bar?

Hey I'm completely fine with stupid questions as long as you can help me out lol ^_^.

Ok, I'm using 9.10.
the output is this: ok I can't get the damn output cause I can't open odts in Windows I guess...
The wireless switch is all well and good lol.
and no, I can't see the networkmanager thing (the two computer screens)

---

### Post by rossmoore on 2010-01-20
You've lost me - what's odts? And why would you need it run that terminal command on your ubuntu computer? Is this something to do with getting the output from the terminal to a windows machine that is connected to the net (i.e. the one you're typing on)? Can you connect with ethernet temporarily?
I'm just looking for the name of the wireless card.

If you can't see the two computer screens (or any other symbol like the network power symbol) then we have a problem with networkmanager. In addition to lshw, give us the output of:
ifconfig
ps -ef | grep network

and also what happens if you type:
nm-applet

That should launch the network manager applet, and it will post warning/error messages telling you what's going on in the terminal.

---

### Post by Sephenon on 2010-01-21
> **rossmoore said:**
> You've lost me - what's odts? And why would you need it run that terminal command on your ubuntu computer? Is this something to do with getting the output from the terminal to a windows machine that is connected to the net (i.e. the one you're typing on)? Can you connect with ethernet temporarily?
I'm just looking for the name of the wireless card.

If you can't see the two computer screens (or any other symbol like the network power symbol) then we have a problem with networkmanager. In addition to lshw, give us the output of:
ifconfig
ps -ef | grep network

and also what happens if you type:
nm-applet

That should launch the network manager applet, and it will post warning/error messages telling you what's going on in the terminal.


When I said odts I meant the .odt file type that is used by open office which is what I saved what Terminal said when I input that command with.

And if I don't run the command on my Ubuntu computer, where should I type that command at?  On my windows OS?

Oh, and I'm almost completely positive that I have a Broadcom card.

---

### Post by rossmoore on 2010-01-21
Ah, I see. So if you're using OpenOffice to transfer the information from one machine to another (Windows) machine, you can Save As .doc format. Once you've transferred the output of the command from one machine to the other, just copy and paste the text so that we can easily review the results.

I also see I missed out the word "to":
"And why would you need it **to**run that terminal command on your ubuntu computer?"
You should be running the command in the terminal on your Ubuntu computer!

Let's see the output of the commands and then we can check on the support available and get you some links to appropriate "How To" tutorials that I'm sure someone will have written.

---

### Post by patty88 on 2010-01-21
hi ppl..
new with ubuntu and all, have the same problem with the wireless network and im also using a dell xps m1330.. after having upgraded to ubuntu 9.10, the network tab says my wireless is disabled.. 
help will be much appreciated.. thnx :)

---

### Post by Sephenon on 2010-01-23
Ok got it converted.  Sorry.  Busy with school lately.  Here ya go see if you guys can make some sense of this thing:

sephenon@MattsLaptop:~$ lshw -C networkWARNING: you should run this program as super-user.  *-network                      description: Network controller       product: BCM4312 802.11b/g       vendor: Broadcom Corporation       physical id: 0       bus info: pci@0000:0c:00.0       version: 01       width: 64 bits       clock: 33MHz       capabilities: bus_master cap_list       configuration: driver=b43-pci-bridge latency=0       resources: irq:17 memory:f6cfc000-f6cfffff  *-network       description: Ethernet interface       product: NetLink BCM5906M Fast Ethernet PCI Express       vendor: Broadcom Corporation       physical id: 0       bus info: pci@0000:09:00.0       logical name: eth0       version: 02       serial: 00:21:9b:cf:13:b9       width: 64 bits       clock: 33MHz       capabilities: bus_master cap_list ethernet physical       configuration: broadcast=yes driver=tg3 driverversion=3.99 firmware=sb v3.04 latency=0 multicast=yes       resources: irq:30 memory:f69f0000-f69fffff

---

### Post by rossmoore on 2010-01-23
Hi Sephenon,

Yes, I see your particular card has problems in Karmic. Here's a link to a post discussing some fixes - people seem to have had hit and miss success.
[http://ubuntuforums.org/showthread.php?t=1309760&page=1](http://ubuntuforums.org/showthread.php?t=1309760&page=1)

I'll some up your options in the order you're likely to want to try them:
Connect your laptop to the internet with an ethernet cable, if this is possible. Update and upgrade and all pacakges you can (System->Administration->Update Manager, then click Check, then Upgrade everything it suggests). Once that is complete (and you've restarted if it tells you to), click:
System->Administration->Hardware Drivers
Hopefully it will find your wireless drivers. Activate them and reboot.

If that doesn't work, you should carefully follow the readme.txt guide here:
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
And install the relevant driver (32-bit or 64-bit - let me know if you don't know which you are) according to the instructions very carefully.

Have a go at those 2 options, and come back to us and tell us what happened either way.

---

### Post by Sephenon on 2010-01-30
BUILD AND INSTALLATION INSTRUCTIONS
-----------------------------------

1. Setup the directory by untarring the proper tarball:

For 32 bit: 	hybrid-portsrc.tar.gz
For 64 bit: 	hybrid-portsrc-x86_64.tar.gz

# mkdir hybrid_wl
# cd hybrid_wl
# tar xzf <path>/hybrid-portsrc.tar or <path>/hybrid-portsrc-x86_64.tar.gz

2. Build the driver as a Linux loadable kernel module (LKM):

# make clean   (optional)
# make

When the build completes, it will produce a wl.ko file in the top level
directory.

3: Remove any other drivers for the Broadcom wireless.

There are several open source drivers that are used to drive Broadcom 802.11
chips such as b43 and ssb. If any of these are present they need to be removed before this 
driver can be installed.  Any previous revisions of the wl driver also need to
be removed.

# lsmod  | grep "b43\|ssb\|wl"

If any of these are installed, remove them:
# rmmod b43
# rmmod ssb
# rmmod wl

To blacklist these drivers and prevent them from loading in the future:
# echo "blacklist ssb" >> /etc/modprobe.d/blacklist.conf
# echo "blacklist b43" >> /etc/modprobe.d/blacklist.conf

4: Insmod the driver.

If you were already running a previous version of wl, you'll want to provide a
clean transition from the older driver. (The path to previous driver is usually
/lib/modules/<kernel-version>/kernel/net/wireless)

# rmmod wl 
# mv <path-to-prev-driver>/wl.ko <path-to-prev-driver>/wl.ko.orig
# cp wl.ko <path-to-prev-driver>/wl.ko
# depmod
# modprobe wl

Otherwise, if you have not previously installed a wl driver do this:

# modprobe lib80211
# insmod wl.ko

wl.ko is now operational.  It may take several seconds for the Network Manager
to notice a new network driver has been installed and show the surrounding
wireless networks.

COMMON ISSUES/QUESTIONS
-----------------------

If there is a problem, usually some clues can be gleaned from the system log
via the 'dmesg' command.

Why aren't channels 12 & 13 supported?  The driver only supports the default
locale setting wich is ROW (Rest Of World) which does not include channels 12 or 13.

I see this output, is it harmful?  WARNING: modpost: missing MODULE_LICENSE()
No it is not harmful and it is expected and should be ignored.

Is my Brcm device with PCI Device ID XYZ Supported?  These PCI Device IDs are supported:

	  Device ID	Product Name
          ---------   	-------------
          0x4311  	4311 2.4 Ghz
          0x4312  	4311 Dualband
          0x4313  	4311 5 Ghz
          0x4315  	4312 2.4 Ghz
          0x4328  	4321 Dualband
          0x4329  	4321 2.4 Ghz
          0x432a  	4321 5 Ghz
          0x432b  	4322 Dualband
          0x432c  	4322 2.4 Ghz
          0x432d  	4322 5 Ghz
          0x4353  	43224 Dualband
          0x4357  	43225 2.4 Ghz


ISSUES FIXED AND WHAT'S NEW IN THIS RELEASE
-------------------------------------------
+ Supports Linux kernel 2.6.29, 2.6.30.1, 2.6.31
+ Supports hidden networks
+ Supports rfkill in kernels <  2.6.31


KNOWN ISSUES AND LIMITATIONS
----------------------------
#72238 - 20% lower throughput on channels 149, 153, 157, and 161
#72324 - Ubuntu 8.04: cannot ping when Linux STA is IBSS creator with WEP enabled
#72216 - Ubuntu 8.04: standby/resume with WPA2 and wpa_supplicant causes a continuous 
	assoc/disassoc loop (issue with wpa_supplicant, restarting wpa_supplicant fixes the issue)
#76739 Ubuntu9.04: unable to connect to hidden network after stdby/resume
#76793 Ubuntu9.04: STA fails to create IBSS network in 5 Ghz band
#76814 Wireless option is Grayed out in Network Manager in FC-11-64bit





I have to be honest guys, I have NO idea what any of this means :(  Can someone help me with it please?

---

