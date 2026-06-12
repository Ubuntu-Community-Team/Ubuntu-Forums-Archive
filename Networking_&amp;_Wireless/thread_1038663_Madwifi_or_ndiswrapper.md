---
title: "Madwifi or ndiswrapper?"
date: 2009-01-13
forum: Networking &amp; Wireless
---

### Post by cptrohn on 2009-01-13
Which one is the better option for internal wireless cards?

---

### Post by 2hot6ft2 on 2009-01-13
> **cptrohn said:**
> Which one is the better option for internal wireless cards?
And the card is a what? The OS is what?
Run ```
lspci
```
in a terminal to find out which card

---

### Post by cptrohn on 2009-01-14
> **2hot6ft2 said:**
> And the card is a what? The OS is what?
Run ```
lspci
```
in a terminal to find out which card

The OS is 8.04.1
the card is an Atheros AR242x.

I have ndiswrapper installed, and there is now an option for WiFi but it still is not working I followed the instructions in this link:
[http://ubuntu-snippets.blogspot.com/2008/12/making-atheros-ar242x-wireless-chipset.html](http://ubuntu-snippets.blogspot.com/2008/12/making-atheros-ar242x-wireless-chipset.html)

A wireless connection shows up in network connections, but I still can't see any bars for WiFi being enabled, the enable wireless is checked in the connection manager when you left click on the icon in the upper right hand corner.

When I go to System>>Administration>>Network Tools

The network device is set as Loopback interface (lo)

When I change this to wireless interface (wlan0) and clicked the configure for the wirless I got this error message :    The interface does not exist.


So this means that the system is still not recognizing my card in Hardy right?  Even with the ndiswrapper installed?

---

### Post by cptrohn on 2009-01-14
> **cptrohn said:**
> The OS is 8.04.1
the card is an Atheros AR242x.

I have ndiswrapper installed, and there is now an option for WiFi but it still is not working I followed the instructions in this link:
[http://ubuntu-snippets.blogspot.com/2008/12/making-atheros-ar242x-wireless-chipset.html](http://ubuntu-snippets.blogspot.com/2008/12/making-atheros-ar242x-wireless-chipset.html)

A wireless connection shows up in network connections, but I still can't see any bars for WiFi being enabled, the enable wireless is checked in the connection manager when you left click on the icon in the upper right hand corner.

When I go to System>>Administration>>Network Tools

The network device is set as Loopback interface (lo)

When I change this to wireless interface (wlan0) and clicked the configure for the wirless I got this error message :    The interface does not exist.


So this means that the system is still not recognizing my card in Hardy right?  Even with the ndiswrapper installed?

Hello?  Anybody?  LOL

Would removing ndiswrapper and trying madwifi be the answer here?

---

