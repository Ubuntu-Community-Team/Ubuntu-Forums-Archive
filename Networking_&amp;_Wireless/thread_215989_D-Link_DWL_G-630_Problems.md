---
title: "D-Link DWL G-630 Problems"
date: 2006-07-14
forum: Networking &amp; Wireless
---

### Post by masonj7 on 2006-07-14
Dell Inspiron 9100 installation of Ubuntu worked perfectly except for the wireless card.  When I insert the card, there are no lights to say that the card even has power.  Is this a problem with the slot itself not being recognized or just that the drivers for that card are not installed properly.

Also, is there a way to install the needed items without using apt-get or other net searching tools?  I currently cannot log on using the laptop, but can burn cd's with all needed files.

---

### Post by infoburner on 2006-07-14
can you run the command "lspci" (without the quotes) and post the result back here?

---

### Post by tturrisi on 2006-07-14
The newer dlink 630 cards have an atheros chipset, which requires the mad-wifi drivers in linux.  These drivers are not installed by default.  You will need to install the linux-restricted-modules for your kernel via apt or synaptic.  Or download the rstricted modules & burn to a cd.

---

### Post by masonj7 on 2006-07-15
that is the lspci command information.  i have tried to install the madwifi stuff, but was unable to correct the problem (probably did it wrong).  thanks for any help.



0000:00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
0000:00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
0000:00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
0000:00:1f.6 Modem: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Modem Controller (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
0000:02:00.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
0000:02:01.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
0000:02:01.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller

---

### Post by infoburner on 2006-07-15
go to [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=linux-restricted&searchon=names&subword=1&version=dapper&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=linux-restricted&searchon=names&subword=1&version=dapper&release=all)
to see a list of the module packages. type `uname -r` to see what kernel you are running. the package you want will be called "linux-restriced-modules-(the output of that command)" 

for example, when i run uname -r i get 2.6.15-26-k7, so i want "linux-restriced-modules-2.6.15-26-k7"

when you click on that package, download the package at the bottom. you will also need to download all the packages listed above which are marked with a red circle, with the exception of the actual linux image. burn all of this to a cd. once you get it to the destination laptop, cd into the directory with all the files you downloaded and type "dpkg -i *.deb". it may tell you that dependencies havent been met so you may  need to install them one at a time with dpkg -i.

---

### Post by masonj7 on 2006-07-17
I have already installed that version of the linux restricted modules through the synaptic program, but it did not do anything to help.  is that supposed to make the card work automatically, or am i supposed to configure something else?

---

### Post by tturrisi on 2006-07-17
Did you reboot after installing the restricted-modules?
Does the 630 card have any lights on it?

1. rt click an empty area of the panel.
2. select "add to panel".
3. add this to panel:  System & hardware > Network Manager
4. rt click Network Manager & select "Properties".
5. click on Configure button & setup your connection.

---

### Post by masonj7 on 2006-07-17
I have restarted many times after installing, but no power or activity lights come on.  I have also tried using the network tool,  but the wireless card does not show up in the connections list like the ethternet and modem.

Card works fine in the dual boot windows xp.

any other options?

---

### Post by tturrisi on 2006-07-17
what's the version number of the dwl630 you have?
does it look like this:

[IMG]http://members.cox.net/aturrisi/dwl630.jpg[/IMG]

---

### Post by masonj7 on 2006-07-17
no, H/W Ver: A1  F/W Ver: 2.2.0.11

---

### Post by tturrisi on 2006-07-17
ok.
the dwl6**3**0 rev **E1** uses has a ralink chipset and uses these drivers:
[http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page](http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page)

It's possible your card also has that chipset.  Other dwl630s have an atheros chipset & use mad-widi drivers.

The dwl6**5**0 rev **A1** uses the ACX111 chipset and acx100 driver.

Let's take a look at your hardware & devices.  Post the results of these commands separately:

sudo lshw -businfo

lspci -v | grep Ethernet

lsmod | grep ath  (sees if mad-wifi driver is loaded)

sudo iwconfig

---

