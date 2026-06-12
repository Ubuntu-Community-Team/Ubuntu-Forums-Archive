---
title: "Dell Inspirion e1705 laptop using ubuntu 12.10; no wireless"
date: 2013-01-13
forum: Networking &amp; Wireless
---

### Post by cselinux on 2013-01-13
I have downloaded ubuntu 12.10 and I am having to use a wireless usb to connect to the internet. I get no connections when I am not using the usb. This specific laptop has a broadcom 4311 wireless card if that helps?

Please help!

---

### Post by ahallubuntu on 2013-01-13
You should be able to find instructions (look at the sticky at the top) to install the correct Broadcom driver.  Or just install an Intel wireless card.  I have a spare E1705 and did that.  Easy to access wireless card from the bottom: just a couple of screws, snap off old antenna wires, snap new ones back on.  Lots of demos on YouTube.

I put an Intel WiFi Link 5100 in it (802.11n).  Works automatically in Ubuntu.

You want a full height card not a half height; doesn't have to be a "Dell" version of the 5100.  but don't get the Lenovo/HP version.    Get a used one from eBay or Amazon probably for about $10 USD, maybe less.

---

### Post by cselinux on 2013-01-14
> **ahallubuntu said:**
> You should be able to find instructions (look at the sticky at the top) to install the correct Broadcom driver.  Or just install an Intel wireless card.  I have a spare E1705 and did that.  Easy to access wireless card from the bottom: just a couple of screws, snap off old antenna wires, snap new ones back on.  Lots of demos on YouTube.

I put an Intel WiFi Link 5100 in it (802.11n).  Works automatically in Ubuntu.

You want a full height card not a half height; doesn't have to be a "Dell" version of the 5100.  but don't get the Lenovo/HP version.    Get a used one from eBay or Amazon probably for about $10 USD, maybe less.


Do I need to buy another one? Or is it possible to find and update drivers using the terminal?

---

### Post by ahallubuntu on 2013-01-14
Here's the "sticky" for Broadcom card issues that is posted at the top of this forum:

[http://ubuntuforums.org/showthread.php?t=2090138](http://ubuntuforums.org/showthread.php?t=2090138)

No, you don't have to buy another card if you can get it to work following the instructions in that link - I just suggested it because it's easy and probably cheap.  And then you'll never have to worry about wireless card compatibility issues again.  As a bonus, you'll be upgrading to an 802.11n card from 802.11g if you get the card I recommended.

---

### Post by cselinux on 2013-01-14
> **ahallubuntu said:**
> Here's the "sticky" for Broadcom card issues that is posted at the top of this forum:

[http://ubuntuforums.org/showthread.php?t=2090138](http://ubuntuforums.org/showthread.php?t=2090138)

No, you don't have to buy another card if you can get it to work following the instructions in that link - I just suggested it because it's easy and probably cheap.  And then you'll never have to worry about wireless card compatibility issues again.  As a bonus, you'll be upgrading to an 802.11n card from 802.11g if you get the card I recommended.

Sounds great I might consider that if I keep having issues :) Where do I find the synaptic package manager? I was looking through another forum and it called for me to open it but I don't know where to find it?

---

### Post by bkratz on 2013-01-14
Look here too--these are easy

[http://askubuntu.com/questions/228821/bcm4311-wireless-not-working-with-drivers-installed](http://askubuntu.com/questions/228821/bcm4311-wireless-not-working-with-drivers-installed)

---

### Post by cselinux on 2013-01-15
> **bkratz said:**
> Look here too--these are easy

[http://askubuntu.com/questions/228821/bcm4311-wireless-not-working-with-drivers-installed](http://askubuntu.com/questions/228821/bcm4311-wireless-not-working-with-drivers-installed)


That did it!! Thank you so much!!!

---

### Post by bkratz on 2013-01-15
> **cselinux said:**
> That did it!! Thank you so much!!!



Sure glad it worked for you, enjoy!

---

