---
title: "Aspire One running Ubuntu 8.10"
date: 2009-02-23
forum: Networking &amp; Wireless
---

### Post by index.dat on 2009-02-23
Greetings. 

I`ve installed Ubuntu version 8.10 on a thumbdrive but Ubuntu seems unable to detect my wireless connection. I know it`s working well because I can access it from windows.

I tried configuring a wireless network by using the information on the modem but I still couldn`t do anything about it.

The following is what is written on the modem:
1)-The SSID
2)-WEP (26 alphanumeric characters)
3)-WAN
4)-LAN

My machine is an Acer Aspire One, so the network card is an Atheros one.

Thank you very much.

---

### Post by hiddensoul on 2009-02-23
There is a great howto on the Ubuntu forums, the link is [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

There is a section there that will help you get wireless running. I am using the madwifi driver on My AAO and it works great

From the article....

Recommended to use the most recent snapshot of madwifi-hal from [http://snapshots.madwifi-project.org/](http://snapshots.madwifi-project.org/)

[I]wget [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz)
sudo apt-get install build-essential linux-headers-$(uname -r)
tar -xzf madwifi-hal-0.10.5.6-current.tar.gz
cd madwifi-hal-0.10.5.6*/
make
sudo make install
sudo modprobe ath_pci[/I]

You may have to append ath_pci to /etc/modules:
[I]
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
ath_pci[/I]

Hope this helps you with your AAO, they are a great little sub notebook

---

### Post by buyone on 2009-02-23
Thank you for the clear instructions. Ubuntu 8.10 Wifi is now working on my AAO.

---

