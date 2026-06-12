---
title: "Network card diagnostics"
date: 2011-03-22
forum: Networking &amp; Wireless
---

### Post by DrPL on 2011-03-22
Hi,
My wife has just informed me that the internet at home has gone down; the tabs in Firefox display "page cannot be displayed" and even a reboot, closing down of firefox
etc. won't help. She's a bit of a technophobe so I am looking forward to an evening
of misery when I get home.
She tells me that the lights on the router look OK so I am suspecting that it is a PC problem. If it is, are there any commands, other than "ping" to test my network, and to test my network card?
 
Thanks!
 
Paul

---

### Post by conneco on 2011-03-22
I usually start with

ifconfig - check that your eth0 is up and you have an ip if no IP then

dhclient3 - check that your getting DHCP leases okay

ping [router] if that goes through

ping [[www.google.co.uk]](www.google.co.uk])

tracert - can show you a route to a host (not needed to test net to be honest)

ifconfig and ping are the best two tools to test network connectivity

---

### Post by Hippytaff on 2011-03-22
also 
show network device info```
lshw -C network
``` like ifconfig (or ipconfig in windows) but for wireless```
iwconfig
``` -```
lscpi | -i grep netw
``` will display the network device chipset so you can fin the name of the driver
```
lsmod | grep -i name-of-the-dirver
``` to see if the driver is installed.
 
Let us know how it goes and what you encounter...might be able to lend a hand :-)
 
edit -> I have a wireless diagnostic script to save maually typing these commands. I haven't got the actual file here in work, but it is in [this thread]("http://ubuntuforums.org/showpost.php?p=10564143&postcount=7"). You would just need to copy it to Gedit text editor -> save as script.sh. then close Gedit, right click the file and check the executable option in permissions. then open a terminal and do ```
./scrtipt.sh
``` It will output the results to a text file called Wireless-Results.txt. If you post that we will be able to see whats what and start trouble shooting

---

### Post by DrPL on 2011-03-23
Hi Hippytaff,
Sadly, it seems that I can't connect to the internet, so I can't download your script to try it :(
 
@Hippytaff and Conneco,
 
My wife got some instructions from Sky's helpdesk but didn't know how to implement them.
She was urged to try "ping 192.168.0.1" and see that the loss value was; if 100%, remove cookies, turn off firewall etc, check cable etc.
 
I've now done all these.
The ping command to that IP recorded 0% packet loss.
 
---
 
I tried some of the commands suggested in this thread:
 
I tried "ping 64.233.169.104" but I get "Destination net unreachable"
 
"lsmod | grep -i name-of-the-dirver" (I also used "driver"!) produced nothing
 
ifconfig produced a lot of stuff, but next to "eth0" amongst the gubbins was
UP BROADCAST RUNNING MULTICAST
inet addr: 192.168.0.2
BCast 192.168.0.255
Mask: 255.255.255.0
 
dhclient3 produces: Rx packets: 85  0 dropped 0 overrun 0 frame
 
I can click on the internet icon on the top right hand corner of the screen, near to the
time, and get "Auto eth0 connection established" and its IP address is 192.168.0.2
 
I'm stumped.

---

### Post by Hippytaff on 2011-03-23
I think we need to back up a bit. Can you post output of ```
lspci | grep -i netw
```  This will tell me what network card you have. From that we can establish if it is one of the ones that tend to be a pain in the rear and try to sort it, if not we can move on

---

### Post by DrPL on 2011-03-23
I'll have to post it tomorrow when I get back to my work PC.
 
My PC has worked quite happily for some 9 months and all of a sudden, this happens!

---

### Post by Hippytaff on 2011-03-23
So the wireless worked without any problems originally? You didn't have to install any drivers?

---

### Post by DrPL on 2011-03-23
It was working fine, and then it stopped!

---

### Post by Hippytaff on 2011-03-23
I'll need to know the chipset, but did an upgrade cause it to stop?

---

### Post by DrPL on 2011-03-24
I did lspci | grep -i netw but it came up with nothing, so I did just "lspci"
and I got that the machine has:
Ethernet Controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)
 
As for the circumstances:
On Monday evening, I was happily on the internet and had a couple of tabs on Firefox open downloading something. I noticed that it was taking longer than necessary...the computer rebooted soon afterwards. When it came back up I could not access the internet.
 
I didn't do any explicit upgrades, but I have noticed that the machine often downloads and installs updates to software when it feels like it. On one occasion I was wondering why the machine was so slow...and doing a "ps" I found out that a new version of the X server had been downloaded and was being installed. I have also found that the machine sometimes has a red button on the top left hand corner of the screen (this is the part by which you can shut down, logout etc.), indicating that a reboot is required after an unscheduled upgrade. So God knows what happened.

---

### Post by Hippytaff on 2011-03-24
That is you're ethernet controller. A wireless controller should also apprear with lspci. It should come under network controller. We need this info to see what chipset you have to go any further. If this isn't showing up there are a number of reasons that this might happen...the worst being hardware faliure.

The updates as you have them set up are fine...I wouldn't worry about it...but if you have specific drivers installed, (Broadcom, Nvidia) sometimes you have to reinstall them after a kernel upgrade (an upgrade which will turn that icon red for reboot) so finding that line in lspci which beins with - Network controller, would be useful :-)

---

### Post by Hakunka-Matata on 2011-03-24
> **Hippytaff said:**
> That is [COLOR=Red]you're[/COLOR] ethernet controller. A wireless controller should also apprear with lspci. It should come under network controller. We need this info to see what chipset you have to go any further. If this isn't showing up there are a number of reasons that this might happen...the worst being hardware faliure.

The updates as you have them set up are fine...I wouldn't worry about it...but if you have specific drivers installed, (Broadcom, Nvidia) sometimes you have to reinstall them after a kernel upgrade (an upgrade which will turn that icon red for reboot) so finding that line in lspci which beins with - Network controller, would be useful :-)

[COLOR=Red]your[/COLOR]

---

### Post by DrPL on 2011-03-24
I didn't see any category when I did lspci about network or wireless cards. This is getting me worried
as, if there is a hardware fault, I am venturing into unknown territory. I simply don't have a clue what to do
and had my fingers burnt badly last year when I bought some RAM that should have been compatible with my PC.
It wasn't (got my money back by selling the memory on Ebay!) and am wary about buying any replacement network
cards etc. that won't be compatible.
Any suggestions more than welcome. It now looks like I am on a certain creek without a certain paddle!

---

### Post by Hippytaff on 2011-03-24
> **Hakunka-Matata said:**
> [COLOR=red]your[/COLOR]
 
ok..pedant ;-)
 
DrPL - Does the wireless work with any other OS (do you have windows on the same machine to try it with) or try from a live CD. It might be that Udev or Dbus is just not picking it up.

---

### Post by DrPL on 2011-03-24
I don't have Windows, but I do have the Ubuntu installation disk (got it from the Linux Emporium); I think that has a live install on it. As long as it doesn't wipe the disk it should be OK (?)

---

### Post by Hippytaff on 2011-03-24
The live cd will run from the CD. When given the option to try or install choose try. You current setup will not be affected in any way. See if that can see [COLOR=red]your[/COLOR] ;-) wireless device by doing```
lspci | grep -i net
```

---

### Post by DrPL on 2011-03-24
I'll try it when I get home and report back tomorrow!

---

### Post by Hippytaff on 2011-03-24
Just to make sure - it's  not a wireless usb device is it?

---

### Post by DrPL on 2011-03-24
No its plugged into a Sky router using Cat5 cable.

---

### Post by Hippytaff on 2011-03-24
So its ethernet not wireless? scrap my earlier post. Try```
sudo ifconfig eth0 up
```
and can you post the output of```
sudo lshw -C Network
```
 
thanks

---

### Post by DrPL on 2011-03-25
I can't find my Ubuntu 10.4 disk, dammit, but I did what you said and got:
 
 
lshw -C network
description: Ethernet interface
product: 82540 EM Gigabit Ethernet Controller
physical id: c
bus info: [EMAIL="pci@0000:02:0c.0"]pci@0000:02:0c.0[/EMAIL]
logical name: eth0
version: 2
serial: 00:08:74:f7:a8:72
size: 100 MB/s
capacity: 1 GB/s
width: 32 bits
clock: 66 MHz
capabilities: pm pcix msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt-fd 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k5-NAPI duplex=full firmware=N/A ip=192.168.0.2
               latency=64 link=yes mingn=255 multicast=yes port=twisted pair speed=100 MB/s
resources: irq=18 memory: ff6e0000 - ff6ffff  
ioport: dcc0(size=64)

---

