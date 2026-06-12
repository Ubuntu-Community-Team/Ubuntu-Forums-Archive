---
title: "Wireless on an Acer Aspire One ZG5"
date: 2009-04-21
forum: Networking &amp; Wireless
---

### Post by jarede on 2009-04-21
Recently decided to wipe my netbook's windows install and put ubuntu on it as I tend to not use the laptop for much more than taking notes in class and figured it'd be a nice test PC.

After looking around it seemed that wireless on 8.10 was flaky so I went with Jaunty, but after a few hours of googling and searching these forums I've still been unable to get wireless working.

Well it did work for about five minutes on the first install but after that it have not worked with wireless networks completely grayed out even though their are plenty of networks in range. 

I attempted blacklisting acer_wmi in /etc/modprobe.d/blacklist.conf but that did nothing. Tried everything on the [Acer Aspire One community page]("https://help.ubuntu.com/community/AspireOne") as well. So any ideas?

lspci -v info
> 03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Foxconn International, Inc. Device e008
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at 55200000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [60] Express Legacy Endpoint, MSI 00
	Capabilities: [90] MSI-X: Enable- Mask- TabSize=1
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Virtual Channel <?>
	Kernel driver in use: ath5k
	Kernel modules: ath5k


Edit: the blacklisting listed in the second post fixed it and deleting the auto ethernet connect fixed issues with connecting

---

### Post by jarede on 2009-04-22
seems adding ath_pci and ath_hal to the blacklist and adding ath5k to /etc/modules at least allows me to connect now, but it presents another problem.

Wireless says I'm connected but after about 5 minutes of being connected nothing loads. Only way to get things to load is to restart the laptop.

---

### Post by mstoutenburg on 2009-06-12
I have the aspire one zg5 and had some troubleshooting with wifi.. I found removing ath5k from /etc/modules and adding acer_wmi, ath5k, ath_hal to the black list was a start. I also had to go to system > administration> hardware drivers " disable madwifi driver" and then open terminal and follow the 8.04 madwifi instructions..

wget [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz)
sudo apt-get install build-essential linux-headers-$(uname -r)
tar -xzf madwifi-hal-0.10.5.6-current.tar.gz
cd madwifi-hal-0.10.5.6*/

go to madwifi directory and in the scripts directory type sudo sh madwifi-unload 

once that is done type sudo make and sudo make install.

reboot and your wifi will not casue the infomouse kernal panic.. 

as for the wireless led does not work use the ubuntu 8.04 intrepid wifi instructions if you want it to work.

---

### Post by mstoutenburg on 2009-06-12
wireless does not come backup after going in to suspend mode. Disabling and re-enabling adapter seems to bring adpter up but cannot scan or see access points.

---

### Post by carcar1 on 2009-06-12
If this is using the atheros ar5007eg then ndiswrapper works great :)  I have had very few problems with it the most annoying one is low signal but that might be might system as I have a regular laptop.  Try this [https://launchpad.net/auto-ndiswrapper]("https://launchpad.net/auto-ndiswrapper")

---

### Post by mstoutenburg on 2009-06-12
this is using madwifi.. I found disabling wifi from network manager and doing a sudo modprobe ath_pci re-enables wifi and connects.

---

### Post by mstoutenburg on 2009-06-12
to shotcut this I made a script in gedit 

sudo ifconfig wifi0 down
sudo ifconfig wifi0 up
sudo modprobe ath_pci

named it wifi-suspend and did a chmod a+x to make it executable with sh.. works good for me.

is there a way to automate this when coming out of suspend mode would be a good fix for these zg5 models.

---

### Post by mstoutenburg on 2009-06-12
carcar1 this is a aspire one zg5 or aa110 mini 9inch from acer shipped with linpus lite. and all those other wifi fixes did not work for me.. I trouble shot for a while to get the wifi to work. I chose the tried and true method that worked. 8.04 will use the ath5k until the latest update then kernel panic sets in. So this looks like the best method I see to keep up with updates and still gt wifi working without crashing on login. you have to do the above steps with madwifi and make clean instead of make to get wifi back but works.

---

### Post by mstoutenburg on 2009-06-12
back to script. to make this easy and accessible with netbooks I have right clicked and edited menu. I put my script in favourites to run with terminal.

---

