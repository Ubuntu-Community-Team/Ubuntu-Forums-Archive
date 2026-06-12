---
title: "ath5k hardships: wireless randomly stops working after boot, after suspend,..."
date: 2009-01-02
forum: Networking &amp; Wireless
---

### Post by my_key on 2009-01-02
I have an asus x51rl laptop which has the same wireless card as the eeepc (the 5007 revision that's wrongly recognised as a 5006). 
```

Lspci:
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

```

I run it with the ath5k driver from linux-backports-modules-intrepid-generic as was suggested by the intrepid release notes. I know this driver holds several bugs and I've contributed to several of the bugreports in the launchpad bugtracker, but what I wan't to know is if the way I'm running it is fine. Because I have nearly every problem a wireless card can have: sometimes when I boot Networkmanager says there are no networks, sometimes the card isn't recognised at all. Every time that I suspend or hibernate, networking capabilities are lost. 

Is there a known way to unload the ath5k at suspend? Because I haven't been able to figure it out. Is the ath5k driver from linux-backports-modules-intrepid-generic package still the preferred driver for this card? Do people have had better luck with the madwifi driver with binary blob? Preferably I wouldn't use ndiswrapper.

---

### Post by carml on 2009-01-02
I used ndiswrapper and it solved my problem with my Atheros,the others I tried at my very first period (a few after installing Ubuntu) follow.
1.People says that Madwifi works,
2.other people used the driver found here [http://wireless.kernel.org/en/users/Download#DownloadlatestLinuxwirelessdrivers,let](http://wireless.kernel.org/en/users/Download#DownloadlatestLinuxwirelessdrivers,let) all people know if one of the suggestions I wrote worked for you. :)

---

### Post by my_key on 2009-01-02
Does ndiswrapper work after resume/suspend? I tried nearly a year ago to find a windows driver for this laptop, but I found a working madwifi driver first. I prefer this one, because that way I can monitor my network's security, ndiswrapper just doesn't have the same capabilities. The only annoying thing with this driver is that you have to recompile and insert the module on every kernel upgrade. For the rest it worked fine. Suspend/resume worked.

Since Intrepid the ath5k driver was advertised during development, but was later left out for compatibility reasons. I really want the ath5k driver to work since, as is my understanding, it doesn't contain the closed binary hal, and there's no need to compile modules (which means less rebooting and getting more work done).

Guess it's best to wait a little longer and revert to the madwifi drivers at the moment. Because ath5k makes you carry around external usb wifi adaptors. :D I always have a cheap spare one which uses the zydas driver handy, but the atheros card is faster and gets a better signal so I rather had that one working.

---

