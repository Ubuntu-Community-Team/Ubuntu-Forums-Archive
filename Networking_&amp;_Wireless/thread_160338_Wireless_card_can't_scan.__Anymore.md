---
title: "Wireless card can't scan.  Anymore?"
date: 2006-04-14
forum: Networking &amp; Wireless
---

### Post by JDHarms on 2006-04-14
My wireless card is a Dell Truemobile 1150 card.  It shipped with my laptop.  

I installed Ubunto this past February, and it's worked great since.  But, recently, I can't pin down an exact date, my wireless card quit autoconnecting to my network.  When I run:

sudo iwlist eth1 scan

I get this:

eth1      Interface doesn't support scanning : Operation not supported

The odd thing is, my laptop used to autoconnect!  Just a month ago, I was in a hotel, and it autoconnected to the hotel's wireless network.  Why doesn't it now?  Is it possible that I turned it off?  I'm going to try booting off the live CD, too see if it autoconnects then, and I'll post back with that information.  Until then, I'd appreciate any help!

---

### Post by JDHarms on 2006-04-14
Nope.  That's odd.  I booted off the 5.10 Live CD, and no autoconnect.  This is very frustrating, becuase when I get on, I don't always no what the ESSID is in hotels, libraries and stuff like that.  

Any help would be greatly appreciated!

---

### Post by totalllama on 2006-04-15
Hi there,  Im by no means an expert in Linux however why not try scanning with wlan0.  On a laptop normally eth1 is the Nic (in my experience)

i.e. #sudo iwlist wlan0 scan

what is the output from the command #ndiswrapper -l?

Cheers
J

---

### Post by JDHarms on 2006-04-16
[QUOTE=totalllama]Hi there,  Im by no means an expert in Linux however why not try scanning with wlan0.  On a laptop normally eth1 is the Nic (in my experience)

i.e. #sudo iwlist wlan0 scan

Output:

wlan0     Interface doesn't support scanning.

what is the output from the command #ndiswrapper -l?

No drivers installed

Cheers
J[/QUOTE]

Thanks for your help, I filled in the input above.  Any more suggestions?  By the way, I'm fairly sure my wireless card is eth1

Daniel

---

### Post by JDHarms on 2006-04-20
Bump

---

### Post by shanep on 2006-04-21
Try this:

Login as root and open up your network config file in file browser.  (etc/network)

This is how mine is setup.  Ive put bold around the parts you may need to add.

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
	**map wlan0**
# The primary network interface
iface eth0 inet dhcp
**iface wlan0 inet dhcp**
**wireless_keymode open**

**auto wlan0**

auto eth0


---------

Save and try scanning again.   Otherwise it could also be a hardware malfunction.

---

