---
title: "AR242x Failing to work after installation of wicd"
date: 2009-08-11
forum: Networking &amp; Wireless
---

### Post by Iacoi on 2009-08-11
Currently running Ubuntu (Jaunty) on an HP G60-455DX. Been using Ubuntu for three weeks or so without flaw. I recently installed wicd to replace network-manager-gnome, which resulted in my computer losing any information about wlan0, ath0, wmaster0, etc. I reinstalled network-manager-gnome and removed wicd, but I still have no wireless internet. lspci shows```
 07:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
```. iwconfig -```
 lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

```Since the loss of Wireless internet I have installed linux-backports-modules-jaunuty and have attempted to use madwifi and ndiswrapper; but to no avail. I used to run ArchLinux, so I checked /etc/modules.d/blacklist but found that the file didn't exist. To my surprize /etc/modules/blacklist didn't exist either. Anyway... kinda lost here so any advice would be greatly appreciated.

EDIT: Forgot to mention that I am dual-booting with Vista, which came with the laptop and I have no CD for. Also I attempted to wipe the Ubuntu partition (In order to preform a clan install), but found that DBAN did not recognize that my main hard drive had been partitioned.

---

### Post by Iacoi on 2009-08-12
Umm... any ideas?

---

### Post by Iacoi on 2009-08-12
Okay I fixed it... here's how to do it.
```
cd /lib/modules/$(uname -r)
```Once there delete all modules used by madwifi...
Then download the most recent file contained inside madwifi-hal-0.10.5.6/ from [http://snapshots.madwifi-project.org/](http://snapshots.madwifi-project.org/)
Put that file onto your desktop and run the following code. 
```
tar -xvf madwifi-hal-0.10.5.6-r########.tar.gz
cd madwifi-hal-0.10.5.6-r########/
```Then simply make the file...
```
make clean
sudo make 
sudo make install
```Then add your module to /etc/modules
```
sudo gedit /etc/modules
```For my wireless card I added "ath_pci" (without quotes)
After all that a simple reboot finishes the job and my wifi card (finally) started working!

P.S. Never install wicd on Ubuntu 9.04 (jaunty) it removes all modules and leaves you without wireless internet!

---

### Post by heuvaladao on 2009-10-03
*Iacoi you sad "*Once there delete all modules used by madwifi...*" but how can i know wich is one is madwifi mod?*

---

