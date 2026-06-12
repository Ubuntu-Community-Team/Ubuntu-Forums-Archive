---
title: "Broadcom BCM4312 doesn't work again--13.04 with kernel update."
date: 2013-06-23
forum: Networking &amp; Wireless
---

### Post by Sequoia Bird on 2013-06-23
*Preface... read if you want: I had 12.04, but updated because it constantly reported a system error (that might have been responsible for crashing applications). 13.04 crashed the computer with a kernel panic error, making it completely useless. I couldn't find a solution on the internet, other than installing the newer kernel "Linux 3.9.0-030900-generic*."[I] The computer doesn't crash anymore (hurrah!) but my wireless card stopped working again. It's the 4th time it's stopped after an update--previous solutions to the problem haven't worked. 
[/I]
I looked through the sticky and tried what they suggested to no avail. Under the Additional Drivers tab,"Software & Updates" says my wireless adapter is using an alternative driver: "Using Broadcom 802.11 Linux STA wireless driver source from bcmwl-kernel-source (proprietary). In Synaptic, I installed "firmware-b43-lpphy-installer" and "b43-fwcutter." Like last time the wireless didn't work,
```
rfkill list
```
...returns nothing.
```
iwconfig
```
returns
```
lo        no wireless extensions.

eth0      no wireless extensions.
```

-------
```

sudo apt-get remove --purge bcmwl-kernel-source
sudo modprobe -rf ssb
sudo apt-get install linux-firmware-nonfree 
sudo modprobe b43
```

Solved it. Taken from another thread. Thanks Hadaka!

---

