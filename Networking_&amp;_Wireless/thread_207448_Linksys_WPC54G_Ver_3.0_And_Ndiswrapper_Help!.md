---
title: "Linksys WPC54G Ver 3.0 And Ndiswrapper Help!"
date: 2006-07-01
forum: Networking &amp; Wireless
---

### Post by Meshuggah27 on 2006-07-01
I got the correct drivers from the linksys website and installed them with ndiswrapper.  It says the hardware is connected but wont let me disable my onboard LAN port and enable my wifi card.  Ive tried almost everything.

My card is a PCMCIA Linksys Wireless-G Notebook adapter model number: WPC54G Version 3.0.

Id greatly appriciate ANYBODYS help on this!

---

### Post by lsyn on 2006-07-10
Wish I could help, but I wanted to say that at least we have the same card.  Are you running 6.06 LTS (drake?)  I have some questions about your experience:

1.  Was your card detected in setup?  Mine was, as eth1.
2.  Did you try to set it up during installation, only to find that the SSID and passphrase don't seem to work?

For me, I can 'configure' the network in a Kubuntu GUI, and then try to activate it.  The GUI just blinks for a second - it turns the interface on and then quickly back off again, with no word as to what went wrong.

Maybe we can figure this junk out.

DJ

---

### Post by Maddoguk2 on 2006-12-31
The easiest way to disable the onboard lan is in the bios. If you disable it then the wireless adapter should work straightaway.

---

### Post by Metaljaz on 2006-12-31
Use this link as a walkthrough for your ndiswrapper installation:

[http://www.tuxmagazine.com/node/1000167](http://www.tuxmagazine.com/node/1000167)

---

### Post by malimx6 on 2006-12-31
Hi,

I am trying to setup WPC54G v.4 on ubuntu 6.06 dapper drake, as well.  I am not very lucky so far.  I have installed ndiswrapper and installed the correct driver of my CD.  First I've tried 2 different drivers from linksys website, including the one mentioned on this page:  [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

When I type in  ndiswrapper -l   I get:

Installed ndis drivers:
lsbcmnds                     driver present

I don't have hardwre present msg :(  The hardware is connected and it was working properly under Win XP.  Anybody has a clue what's going on or how to fix this issue?

Oh, when I type in    lspci   I get on the last line:
0000:06:00.0  Ethernet Controller:  Linksys, A Division of Cisco Systems [AirConn]  INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)

If I type in    iwconfig   I get:

lo                no wireless extensions.

eth0            no wireless extensions.

irda0           no wireless extensions.

sit0             no wireless extensions.


Any help is greatly appreciated!

Thanks.

---

### Post by Metaljaz on 2007-01-01
Try this walkthrough for troubleshooting:

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

### Post by malimx6 on 2007-01-01
Hi, thanks for the link.
So far, I have been successful to get the <driver present, hardware> present msg when <ndiswrapper -l> is executed.
I was going through the troubleshooting on the link you left me and when I type in <lshw> this is what I get:

 *-network UNCLAIMED
          description: Ethernet controller
          product: [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
          vendor: Linksys, A Division of Cisco Systems
          physical id: 1
          bus info: pci@06:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
          capabilities: cap_list
          resources: iomemory:36000800-3600081f iomemory:36000000-360007ff irq:11

There's no driver info :(

If I do ifdown -a then ifup -a this is what I get for wlan0:

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

It looks like the OS cannot recognize the card.

Please help!!!

---

### Post by Metaljaz on 2007-01-01
it sounds like you may have to black list native drivers.
Take a look at your private messages. There are some
instructions that may be helpful.

---

### Post by Metaljaz on 2007-01-02
I took this from another post: Give it a shot. Substitute the users file info with your stuff:

Do you have the Windows drivers for the chipset? If you have them, you can use ndiswrapper to install them and then use the network tool under Preferences|Networking to activate. If you don't the rest is just noise.

I use a Netgear WG111 USB access point, so I can only tell you the pattern that I follow and you will have to try yourself.! Almost the same procedure has worked for other USBs and for PCMCIA cards also.

Install ndiswrapper-utils from the CD or Synaptic. You will need the MAC of the wireless card later. In the console type the following:

* #sudo ndiswrapper -l

* [this looks for installed *.inf files]
* #cd /directory_where_the_INF_and_SYS_files_are_stored

* [note that you must have the INF and SYS files together in the same directory]
* #sudo ndiswrapper -i FILE.inf
* #sudo depmod -a
* #sudo modprobe ndiswrapper
* #sudo ndiswrapper -m

* [that installs the windows driver within the wrapper as part of the kernel]
* #sudo gedit /etc/modules

* add ndiswrapper at the bottom of the list
* #sudo gedit /etc/modprobe.d/blacklist

* add the following at the bottom:

* blacklist islsm

* blacklist islsm_usb

* blacklist islsm_pci

* blacklist prism2_usb

* (this blacklisting may very well be specific for my access point)
* #sudo gedit /etc/iftab

* add the following at the bottom:

* wlan0 mac (insert mac number here)


now close the machine down and reboot, go back to Preferences|Networking and the wireless should now be visible.


Good luck!

---

### Post by malimx6 on 2007-01-02
> **Metaljaz said:**
> I took this from another post: Give it a shot. Substitute the users file info with your stuff:

Do you have the Windows drivers for the chipset? If you have them, you can use ndiswrapper to install them and then use the network tool under Preferences|Networking to activate. If you don't the rest is just noise.

I use a Netgear WG111 USB access point, so I can only tell you the pattern that I follow and you will have to try yourself.! Almost the same procedure has worked for other USBs and for PCMCIA cards also.

Install ndiswrapper-utils from the CD or Synaptic. You will need the MAC of the wireless card later. In the console type the following:

* #sudo ndiswrapper -l

* [this looks for installed *.inf files]
* #cd /directory_where_the_INF_and_SYS_files_are_stored

* [note that you must have the INF and SYS files together in the same directory]
* #sudo ndiswrapper -i FILE.inf
* #sudo depmod -a
* #sudo modprobe ndiswrapper
* #sudo ndiswrapper -m

* [that installs the windows driver within the wrapper as part of the kernel]
* #sudo gedit /etc/modules

* add ndiswrapper at the bottom of the list
* #sudo gedit /etc/modprobe.d/blacklist

* add the following at the bottom:

* blacklist islsm

* blacklist islsm_usb

* blacklist islsm_pci

* blacklist prism2_usb

* (this blacklisting may very well be specific for my access point)
* #sudo gedit /etc/iftab

* add the following at the bottom:

* wlan0 mac (insert mac number here)


now close the machine down and reboot, go back to Preferences|Networking and the wireless should now be visible.


Good luck!


This is what worked for me!!!!  Again, thanks a lot Metaljaz!!!!
I had problems with my driver first.  When I used the original driver off the CD I would get driver present but no hardware present when <ndiswrapper -l> command is used.  I got the driver off this site:
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)
I think this is the driver I used:
[ftp://ftp.support.acer-euro.com/notebook/TravelMate_4000_4500/driver/a802.zip](ftp://ftp.support.acer-euro.com/notebook/TravelMate_4000_4500/driver/a802.zip)
Sorry, can't remember exactly, but the name of the driver (or .inf file) is neti2220.inf.  This gave me driver present, hardware present msg.  After that, I just followed the above steps that Metaljaz left and it worked.

Hopefully this will work for everyone else!

---

