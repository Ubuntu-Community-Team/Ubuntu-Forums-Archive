---
title: "Cannot get wireless on Dell Studio 1535 to work."
date: 2011-01-27
forum: Networking &amp; Wireless
---

### Post by AndyAD on 2011-01-27
I've had Ubuntu 10.04 (CEA Linux) installed on my machine for about a year now, but have never been able to get the wireless to work, despite numerous attempts using the info from threads of similar machines.
Could anyone provide some assistance as I'm beginning to lose patience with it!???

My computer is a Dell Studio 1535,

Wireless card is (from command:lspci): 0c:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)

From iwconfig:
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

For command, lsmod, I don't see any wlan info.

For command lshw, I get:
$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:f6cfc000-f6cfffff



I've tried the built in Broadcom drivers, but nothing!
Can anyone direct me how to finally get wireless sorted??

---

### Post by gordintoronto on 2011-01-27
Do you have a network icon on the top, near the speaker icon? What do you see when you click it? (I mean, exactly what do you see?)

On youtube, there are several tutorials on what steps you should take to connect to a network, have you watched any of them?

---

### Post by AndyAD on 2011-01-27
I left the computer in work so can't be sure, but when the symbol is there, it shows 3 arcs radiating up, (presumably wireless signal strength), but with an exclaimation mark next to it. When clicked on, it goes to wired connections tab. Not sure, but will post actual results tomorrow.

---

### Post by AndyAD on 2011-01-28
Hi, I've just checked:

normally with ethernet connected, it just shows ethernet connection. When that is unplugged I see the 3 arcs and an exclamation mark. When I click on this, a drop down menu says "Wired Networks" and below in faint "Disconnected", below again, it says "VPN Connections".

---

### Post by grahammechanical on 2011-01-28
When you right click that icon is there a tick mark against Enable wireless? Also, is this a laptop? Do you need to switch the wireless adapter on by pressing a key combination?

The problem could be, either the wireless adapter is not switched on in hardware or the OS has not recongnized the wireless adapter and has not installed suitable drivers.

What do you see under System>Administration>Additional Drivers?

Regards.

---

### Post by AndyAD on 2011-01-30
Hi grahammechanical,

This is a laptop, but the wireless is turned on by a switch. When turned off, then on, there is no response. When I click the icon in the bar, there isn't an option for wireless to enable, just the 'Wired networks' 'Disabled' and 'VPN Config'.

When I goto System>Administration>Hardware Drivers, it searches and brings up a box about Proprietary Drivers, listing the Broadcom STA wireless driver. In the box about it, it says that the driver is 'Activated but not currently in use'. (Am I being increadibly rookie about this??)

---

### Post by bkratz on 2011-01-30
Not on my Ubuntu system right now, but if memory serves look at

sudo gedit /etc/modules

and see if it says both wl and lp or just lp. If just lp we will probably have to add the wl here so it will load when booting.

---

### Post by AndyAD on 2011-01-31
Hi, trying that command (sudo gedit /etc/modules), I got a window pop-up with the following:

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc
lp
rtc
ndiswrapper

---

### Post by perspectoff on 2011-01-31
I often get flamed when I suggest this, but try using Wicd instead of Network Manager.

Remove all the network-manager related modules (such as gnome-network-manager is you are using Ubuntu), reboot once, then install wicd. (You will have to be wired to download and install wicd).

I have never had a problem with Wicd, whereas I frequently (still) have problems with wireless and Network Manager.

---

### Post by bkratz on 2011-01-31
> **AndyAD said:**
> Hi, trying that command (sudo gedit /etc/modules), I got a window pop-up with the following:

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc
lp
rtc
ndiswrapper


Well I probably would add a line that says just wl. That is WL in lowercase, which should load the STA driver at boot. Also I would put a # in front of ndiswrapper since it often interferes with the correct driver. The # is like a comment causing that line to be ignored.

Also actually when using gedit (for changes--not just looking around) you really should use gksudo since it is a graphical program. There are many threads that explain why.

See about halfway down this page as one example
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by AndyAD on 2011-02-01
> **bkratz said:**
> Well I probably would add a line that says just wl. That is WL in lowercase, which should load the STA driver at boot. Also I would put a # in front of ndiswrapper since it often interferes with the correct driver. The # is like a comment causing that line to be ignored.

Also actually when using gedit (for changes--not just looking around) you really should use gksudo since it is a graphical program. There are many threads that explain why.

See about halfway down this page as one example
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)


That worked PERFECTLY!!!!

Thanks for all your help, very much appreciated. Cheers for suggestions too.

---

### Post by bkratz on 2011-02-01
> **AndyAD said:**
> That worked PERFECTLY!!!!

Thanks for all your help, very much appreciated. Cheers for suggestions too.


Congratulations!

Please go to the thread tools at the top of the page and mark as solved, just in case it helps someone else in the same situation.

---

