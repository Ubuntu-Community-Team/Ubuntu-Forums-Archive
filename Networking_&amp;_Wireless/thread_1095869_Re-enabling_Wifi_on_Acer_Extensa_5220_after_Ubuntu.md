---
title: "Re-enabling Wifi on Acer Extensa 5220 after Ubuntu update"
date: 2009-03-14
forum: Networking &amp; Wireless
---

### Post by merllin on 2009-03-14
I was suffering from disabled Wifi drivers after updating via automatic updates.

Version Ubuntu 8.04LTS
Machine: Acer Extensa 5220

SOLUTION:

Moved previously downloaded madwif drivers from 'madwifi-hal-0.10.5.6-r3816-20080724' to a new folder with a shorter name called 'madwifi' This stopped a problem with 'make' which said "No rule to make target error STOP" caused I believe by the long foldername (?)

Then I followed instructions at the main Acer Aspire One "how-to"([https//help.ubuntu.com/community/AspireOne110L#WLan]("https://https//help.ubuntu.com/community/AspireOne110L#WLan")) EXCEPT it only worked when I issued every command preceded by 'sudo' See below:

```
sudo make clean
```

then..

```
sudo make
sudo make install
```

then

```
sudo modprobe ath_pci
```
 
======= CRUCIALLY I then RE-BOOTED =======

```
sudo ifconfig ath0 up
iwconfig
```

(Previous to this I was tearing my hair out as the ifconfig ath0 up command failed unless I rebooted)

I can confirm that the instructions for getting the light working on the ACER aspire One also works fine for the Extensa 5220 :D

---

