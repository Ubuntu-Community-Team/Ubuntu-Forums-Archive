---
title: "Bringing ra0 up causes freeze"
date: 2006-02-04
forum: Networking &amp; Wireless
---

### Post by Simoo on 2006-02-04
Hi, I need some help!

I have a Belkin F5D7010 wireless card (which I beleive uses the rt2500 chipset) and it seems that whenever ubuntu attempts to access it the whole system freezes

This is my /etc/network/interfaces:

>
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface
iface eth0 inet dhcp
iface ra0 inet dhcp 
        pre-up ifconfig ra0 up
        pre-up ifconfig ra0 down
        pre-up ifconfig ra0 up
        pre-up ifconfig ra0 down
        pre-up iwconfig ra0 essid "my essid"
        pre-up iwconfig ra0 mode Managed
        pre-up iwpriv ra0 set AuthMode=WPAPSK
        pre-up iwpriv ra0 set EncrypType=TKIP
        pre-up iwpriv ra0 set WPAPSK="my wpa key"
        pre-up ifconfig ra0 up
>

Then when I run "ifconfig ra0 up" the whole system freezes. 

It also freezes if I go in to 'System->Administration->Networking' although thats no use anyway cos I have WPA encryption.

I want to use my Ubuntu! help
thanks
Simon

---

### Post by bscbrit on 2006-02-04
Try to pin-point which command is causing the problem.  I suggest that you first set up your network unencrypted to get the device itself working.  Once you have achieved that, introduce encryption.

If you do not want to go down this particular route. at least comment out the encryption parts of your interfaces and ifup ra0 again.  If it freezes, the problem is in the remaining commands, if not, the problem is with the encryption.  Comment out half of the remaining commands that are causing the problem and repeat.  Eventually you will be left with one or two commands that are the cause of all of your woes.

I would still set it up in stages but that is just my way of doing things.

EDIT By the way, in your interfaces file you are ifconfig up and ifconfig down ra0 twice in succession - is this intentional?

The network GUI doesn't work very well for wireless anyway :D

---

### Post by Lambert on 2006-02-04
The ifconfig statments in your file are causing it, remove all of these.

You're using ifconfig to call it's self and try to do something it's already doing and it is going in a series of loops. The device is going down and then trying to come up. When it comes up it starts over and reads the interface file again, what's the first line, take it down then up, then down, then up......


The only one you might need and want to leave is one down statement which will make sure it's not currently activated, then it will set up everything else and come up at the end after all the pre-up statements.

---

### Post by Simoo on 2006-02-04
Thanks for the help guys.

I tried what you said, removing lines from the interfaces file and it made no difference (I did copy mine from the 'ubuntu howto' page on the rt2500 driver page so it should have been correct anyway - [https://wiki.ubuntu.com/WifiDocs/RalinkRT2500?action=show&redirect=Rt2500WirelessCardsHowTo](https://wiki.ubuntu.com/WifiDocs/RalinkRT2500?action=show&redirect=Rt2500WirelessCardsHowTo))

unfortunately after quickly scanning the driver's forums it seems I have to recompile the kernel and although it gives some tips, I really wouldnt know where to start. 

All I know is "preemption and SMP are not supported for r2500" so I need to recompile with out those??

If  you guys (or anyone) knows an easy way to get a working kernel, or just a card that will work out the box (I would prefere to get mine working) Please leat me know

Thanks
Simon

---

### Post by bscbrit on 2006-02-04
I don't think that you have to recompile the kernel - others have already managed to get this card working with a bog standard ubuntu:

[http://ubuntuforums.org/showthread.php?t=123623](http://ubuntuforums.org/showthread.php?t=123623)

Give it a look.

---

### Post by Simoo on 2006-02-04
Thanks for the link but im confused as to why ndiswrapper is being used to install a card that has native linux support (am I right in thinking ndiswrapper is not altogether native), also I cant see a working conclusion there. 

The open source rt2x00 drivers seem good and have wpa support which I need, is anyone using them?

Thanks again

Simon

---

### Post by Bill Door on 2006-02-09
I have a similar problem:cry: 

machine is a laptop 233MMX with 128 MB ram:rolleyes: 

wireless card is MSI ID number 1814:0201
shows up under lspci -n

driver is rt2500 which shows up under lsmod

when is do lshw the print out is
Sudo lshw –C network
·	*-network DISABLED
·	       description: Wireless interface
·	       product: Ralink RT 2500 802.11 cardbus reference Card
·	       vendor: Ralink
·	       physical id: 0
·	       bus info: pci@01:00.0
·	       logical name: ra0
·	       version: 01
·	       serial: 00:11:09:2a:3f:ef
·	       width: 32 bits
·	       clock: 33MHz
·	       capabilities: bus_master cap_list ethernet physical wireless
·	       configuration: broadcast=yes driver=rt2500 multicast=yes wireless=RT2500 wireless
·	       resources: iomemory:8800000-8801fff irq:10

If i go to System <> admin <> networking 

the networking settings dialog comes up and shows wireless connection then
"the interface ra0 is not configured":-k 

if i click in that item properties comes alive and when i click on properties it freezes before i get to the next dialog box.  I have to switch off and reboot.:evil: 

the light on the wireless card stays on (until i switch off):rolleyes: 

anyone got any ideas.  I have played around with the swap partition and increased it but it makes no difference (someone said that it might!!):cool: 

I have even done the ndiswrapper bit but no difference (have reloaded about 5 times so far):mad:  

I also have no sound could the problems be linked.:???: 

many thanks for any advice

regards  Bill Door

---

