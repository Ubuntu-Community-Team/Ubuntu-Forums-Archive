---
title: "command-line wireless for minimal install"
date: 2012-01-28
forum: Networking &amp; Wireless
---

### Post by angus37 on 2012-01-28
Hello all - 

I am trying to set up wireless on an old Compaq Presario 2100 running 11.10 - since it is an older system, I am trying a command-line based install. So a lot of the GUI-based instructions I have found online don't completely apply.

Here's what I have found in my searches:

lspci -vnn
> 02:00.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)


From this, I take it to mean that I need to install b43-fwcutter and firmware-b43legacy-installer, which I have done. If I am correct, there is an error which requires me to manually download the driver files that these packages normally download. I have downloaded and installed the drivers...and that is as far as I can get. Everything I have seen from this point suggests activating the drivers as such:

>     Step 2.

    Under the desktop menu System > Administration > Hardware/Additional Drivers, the b43 drivers can be activated for use.


Since I have a command-line installation, this isn't an option to me. So, assuming I am on the right track so far, how can I activate the drivers from the command line? AND, if I am not on the right track, could you please help me get there? 

Thanks!

---

### Post by kevdog on 2012-01-29
Your definitely close.

Usually b43 is loaded as a default.  Is this the case for you -- meaning lets investigate:

lshw -C network --- This will list appropriate driver.

If you see anything else listed than b43 for the driver you can unload the driver (or kernel module as its called in linux) by:
sudo modprobe -r <module name>

You can then load b43 by:
sudo modprobe b43

Then take a look and see if its associated with the device with the lshw -C network statement.

---

### Post by angus37 on 2012-01-29
lshw -C network

>   *-network
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 00
       serial: 00:0b:cd:a6:5c:5d
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=full ip=192.168.2.2 latency=90 maxlatency=52 mingnt=11 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:10 ioport:2400(size=256) memory:d0004000-d0004fff memory:54000000-5400ffff
  *-network UNCLAIMED
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: memory:50000000-50001fff


For the wireless card, I don't see a driver listed. Perhaps this is part of the issue?

I went ahead and tried the command

modprobe b43

just to see if anything happened...and my wireless card connected!

I'm going to restart the computer and see if anything changes or if I can replicate the behavior. Stay tuned...

UPDATE: I restarted the computer, tried the "modprobe b43" command again (must be run as sudo) and it worked. So things seem to be working, thank you for the help!

Now that I have the wireless working, what do I need to do so that I don't have to manually start it every time I log on?

---

### Post by nothingspecial on 2012-01-29
The additional drivers app is known as jockey.

There is a cli version known as jockey-text.

Use that.

---

### Post by angus37 on 2012-01-29
> **nothingspecial said:**
> The additional drivers app is known as jockey.

There is a cli version known as jockey-text.

Use that.

I've not heard of jockey before; tried installing it but still not sure how to use it.

I added the line 'b43' in the /etc/modules file and the wireless started up upon reboot.

I'm going to consider this a success unless anyone who knows more than me (which is pretty much all of you) sees a reason to not do this.

---

