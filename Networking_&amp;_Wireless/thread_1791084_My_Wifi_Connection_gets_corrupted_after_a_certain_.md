---
title: "My Wifi Connection gets corrupted after a certain software installation"
date: 2011-06-26
forum: Networking &amp; Wireless
---

### Post by cyper.bg on 2011-06-26
Ubuntu 11.04 32bit
[TP-Link TL-WN821N]("http://www.tp-link.com/products/productDetails.asp?pmodel=TL-WN821N&content=spe") which is listed [HERE]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsTP-Link") as supported using the ar9170usb driver.

So I've done 4 fresh reinstalls and each time after a specific step following [THIS]("http://forum.bitcoin.org/index.php?topic=10608.0") guide my Wireless connection gets corrupted and does not want to work.

The last time I did all the changes in small steps so I can catch the offending one and so after I've executed the code below and restarted my system the wifi went haywire:

> cd ~
sudo apt-get install dkms
wget [http://www2.ati.com/drivers/linux/ati-driver-installer-11-5-x86.x86_64.run](http://www2.ati.com/drivers/linux/ati-driver-installer-11-5-x86.x86_64.run)
sudo sh ati-driver-installer-11-5-x86.x86_64.run --buildpkg Ubuntu/natty
sudo dpkg -i *.deb
sudo apt-get -f install
sudo aticonfig -f --initial --adapter=all
sudo rebootUp until that point everything was working just fine and I was remotely managing my desktop using a Windows VNC Viewer and Ubuntu Remote Desktop.

So could it be that this dkms (whatever that is) is causing the problems? Do I even need to install it for all the other software to work as it is not mentioned in any other bitcoin mining guides?

**I would like to stress out that my connection is configured properly and I am 100% certain of that - as I said [COLOR=Red]it is working like a charm up until the point of executing the commands above and restarting.[/COLOR]**

Any suggestions as the last 3 days have been a nightmare trying to figure out what's wrong after each fresh installation.

P.S - The guide says to execute **sudo aptitude install dkms** but I guess the aptitude package is not installed so I ran **sudo apt-get install dkms** instead. If that makes any difference?

---

### Post by cyper.bg on 2011-06-26
Well after yet another fresh installation I did not install the dkms packkage, but proceeded straight to installing the video card driver using this command ( I downloaded it first):

> sudo sh ati-driver-installer-11-3-x86.x86_64.run

It installed successfully but after the first reboot my wifi connection got corrupted/down.

Here are the logs: [http://paste.ubuntu.com/633324/](http://paste.ubuntu.com/633324/)

Please any help is much appreciated.

---

### Post by cyper.bg on 2011-06-27
Anyone?
Please.

---

