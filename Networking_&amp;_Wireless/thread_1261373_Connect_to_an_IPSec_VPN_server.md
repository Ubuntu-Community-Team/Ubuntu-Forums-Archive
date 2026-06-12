---
title: "Connect to an IPSec VPN server?"
date: 2009-09-08
forum: Networking &amp; Wireless
---

### Post by afowler on 2009-09-08
Hi,

I need to connect to remote network via VPN.

They have given me a username / pw for the VPN and they say it is "IPSec running on windows server".

I tried going to the "network connections"->"VPN" window, but the "add" button greyed out.

How should I proceed?

Thank you,
:)

---

### Post by afowler on 2009-09-10
anybody?

---

### Post by QaysHP on 2009-10-06
You probably want to install the package network-manager-vpnc (and it's dependencies), it will allow you to add IPSec based VPN connections in the menu you are looking at.:)

---

### Post by provomike on 2009-10-08
not on Ubuntu 8.04 LTS - I have tried every suggestion in the book and cannot get a VPN tab.

---

### Post by ertw1 on 2009-10-10
> **QaysHP said:**
> You probably want to install the package network-manager-vpnc (and it's dependencies), it will allow you to add IPSec based VPN connections in the menu you are looking at.:)

Thank you!

---

### Post by QaysHP on 2009-10-13
> **provomike said:**
> I have tried every suggestion in the book and cannot get a VPN tab.

Are you using network-manager and see the other tabs (ie. Wired, Wireless)?
I'm not completely certain as I don't have any machines still running the LTS, but network-manager should be similar.

---

