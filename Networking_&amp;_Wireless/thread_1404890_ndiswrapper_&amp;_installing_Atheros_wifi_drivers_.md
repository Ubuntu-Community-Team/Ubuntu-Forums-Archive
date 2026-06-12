---
title: "ndiswrapper &amp; installing Atheros wifi drivers !"
date: 2010-02-11
forum: Networking &amp; Wireless
---

### Post by alanhutchinson on 2010-02-11
[LEFT]
[/LEFT]
Hi I have bean trying to uzip and install
        the ndiswrappper driver for my Atheros  AR5212/AR5213, well first I can not finde the driver on line, secondly I have tried to unzip the driver from the CD that came with Atheros AR5212/5213 that did not work \"WDA2320.exe\"plus the ndiswrapper help files are not explanatory enough for the different scenarios, thirdly I installed the ndiswrapper interface that installs on the desk top, that worked for a while then stopped altogether, I have bean working on this ,on and off for about a year,my O/S is Debian Lenny Betta -2- i386 I have attached a document coled Atheros doc pertaining to the hard ware in my P/C
thank you.

---

### Post by pytheas22 on 2010-02-12
First off, you're using Debian Lenny, which is different from Ubuntu (they're two different Linux distributions).  If you replaced Debian with Ubuntu version 9.10 (named Karmic Koala), the wireless card should work automatically without any extra effort on your part.  That's the approach I would recommend if you're able to replace your current operating system.

If you need to stick with Debian for some reason, you can try installing the madwifi drivers (note that these are different from ndiswrapper, but should work better than ndiswrapper).  First, download the source code by clicking [this link]("http://downloads.sourceforge.net/madwifi/madwifi-0.9.4.tar.gz").  Save the download to your desktop.  Then run running these commands to install:
```

su
apt-get update
apt-get install build-essential
cd ~/Desktop
tar -xzvf madwifi*
cd madwifi-0.9.4
make
make install
echo ath_pci >> /etc/modules
```

Please post the output of all of these commands so I make sure they proceeded correctly.  After you've finished running them, reboot, and hopefully your wireless card will work.  If it still doesn't, please post the output of:
```

lsmod | grep -e ath -e ndis
sudo modprobe ath_pci
modinfo ath_pci
dmesg | grep -e ath -e wlan
ndiswrapper -l
```

As a word of warning, I've never used Debian so I'm not optimistic about this working on the first try.  But we should be able to figure it out sooner or later.

And again, if it's at all possible to just wipe out your current operating system and replace it with Ubuntu 9.10, that would probably be a much better way to go.  Ubuntu is generally easier to use than Debian, and as I said, your wireless card should work out-of-the-box in Ubuntu 9.10.

---

