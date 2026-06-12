---
title: "cannot connect to hidden wpa2 enterprise"
date: 2009-11-24
forum: Networking &amp; Wireless
---

### Post by Whise on 2009-11-24
i cannot connect to eduroam (university network) after upgrading to karmic anymore.

When i tried to connect to the hidden network the connect button is inactive so i cannot click on it

the password entry is empty (in the connect dialog) but is is also inactive so i cant add a password.

In the network settings i can enter my pass but that doesnt allow me to connect either.

I tried to remove the network and readd it but with no success.

can anyone help out please

---

### Post by Whise on 2009-11-25
anyone?

---

### Post by maxbur on 2009-11-25
I experience an issue similar to yours. Although my current wireless connection uses WEP 128-bit encryption, the network ESSID is hidden like yours. During a fresh install of Karmic yesterday I used the Gnome NetworkManager applet to set up the network connections and all was well.

Booting up today, no wireless connection and NetworkManager won't accept any commands for the wireless card (a Broadcom BCM4328). However, 20 minutes later NetworkManager did establish the connection to the default hidden network on its own and is still working fine 2 hours later.

Are you able to reboot and give your computer 30 minutes or so to try and connect on its own? That would indicate the long connection time is a bug.

Different bugs in previous versions of NetworkManager have always led me to remove it in favour of manual network configuration via the /etc/network/interfaces file, but if the connection time can be reduced it may be worth giving NetworkManager another chance.

---

### Post by Whise on 2009-11-27
i try to wait a bit like you sayd, im not shure if this is a not a bug resolting from the paper cuts implementation

---

### Post by efflandt on 2009-11-27
With hidden SSID, it is possible that Linux does not even know the wireless network is there until someone else connects to it.  Hiding an SSID does not do much from a security standpoint because the SSID is transmitted in the clear during any wireless traffic.  Although, hiding it can make it more difficult to connect to and remain connected, even when you know it is there.

---

### Post by Whise on 2009-12-03
like i said its a university network, i cant change it.

And i always worked in previous versions of ubuntu

---

