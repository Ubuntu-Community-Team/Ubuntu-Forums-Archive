---
title: "Atheros fix and upgrade to 8.10"
date: 2008-12-27
forum: Networking &amp; Wireless
---

### Post by michaelpagz on 2008-12-27
Okay. So I have a Toshiba Satellite A215 s4747 which has an atheros wireless card and I installed 8.04 and got the wireless to work through ndiswrapper and blacklisting the restricted driver. When I upgraded to 8.10 there was an option to not upgrade that specific modification and I chose not to. Upon rebooting after the upgrade the wireless option was still there but the laptop can no longer complete a connection. The network manager shows every wireless as very low and tries to connect but it never works. Is there a separate fix to this issue?  Thank you in advance for your help.

---

### Post by michaelpagz on 2008-12-27
OH! Nevermind. I simply had to install the backports module for intrepid.

---

