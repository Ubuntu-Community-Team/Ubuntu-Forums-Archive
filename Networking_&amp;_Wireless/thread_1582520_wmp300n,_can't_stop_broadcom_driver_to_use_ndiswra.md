---
title: "wmp300n, can't stop broadcom driver to use ndiswrapper"
date: 2010-09-26
forum: Networking &amp; Wireless
---

### Post by sgt.sargent on 2010-09-26
* I'm trying to help a friend with even less experience in Ubuntu or Linux than I have.  She has a Lynksys wmp300n networking card and wants it to work with her new 64-bit system (Ubuntu 9.10).  One of the files needed to use it in ndiswrapper was not on her CD and isn't available from their web site.  After a few days, I found a Compaq driver .exe that contains the file and thought I was home free.  The problem now is that I can't make the broadcom driver the system defaulted to to stop being used.  My steps were:

sudo apt-get install network-manager
sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
***	//got a -> couldn't find "BCMWL564.SYS"
sudo ndiswrapper -r bcml5
***	//got the sys file from a divers for a Compaq card I found a link to
sudo ndiswrapper -l
***	//got nothing back
sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
sudo ndiswrapper -l
***	//bcmwl5 : driver installed
***	//device (14E4:4329) present (alternate driver: ssb)
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m
***	//got -> adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper...
gksudo gedit /etc/modules
***	//added ndiswrapper as the new last line, saved and closed
iwconfig
***	//got ->
***	//lo	no wireless extensions.
***	//
***	//eth0	no wireless extensions.
lshw -C Network
***	// got -> diver=b43-pci-bridge
sudo gedit /etc/modprobe.d/blacklist
***	//added "blacklist b43-pci-bridge" as the only line in the file, save and closed
sudo update-initramfs -k all -u
***	//got -> update-initramfs:Generating /boot/initrd.img-2.6.31-14 generic
***	//rebooted
iwconfig
***	//got ->
***	//lo	no wireless extensions.
***	//
***	//eth0	no wireless extensions.
lshw -C Network
***	// got -> diver=b43-pci-bridge
sudo gedit /etc/modprobe.d/blacklist
***	//confirmed that it still has "blacklist b43-pci-bridge" as the only line in the file
***	//opened a file prowser and confirmed the location and name of the file and that it definately only has that line in the file

* Now at this point I don't understand why the b43-pci-bridge driver is still being used nor what to do about it.


Edit-> Not sure why it added asterisks in place of my false spaces that I used for indentation, but I can't seem to make it stop replacing them (or stop deleting normal spaces or ignoring and not rendering tabs).  Sorry about the strange resulting appearance.

---

### Post by sgt.sargent on 2010-10-18
I found some forum threads where people had blacklisted more things in order to get ndiswrapper wireless drivers working so at this point I've expanded the blacklist list ->
blacklist b43-pci-bridge
blacklist b43
blacklist b43-legacy
blacklist b44
blacklist ssb

So at this point lshw -C Network now gives
*-network UNCLAIMED

I can't seem to get the system to use the bcmwl5 drivers for the card and the searches I've done on "*-network UNCLAIMED" have only turned up people putting drivers in place.  As far as I can tell, the drivers are in place (I've even removed and replaced them a few times, with sudo ndiswrapper -l show them and using -r and -i to remove and replace them) but the system isn't using the drivers and just keeps saying network UNCLAIMED for the card.

---

