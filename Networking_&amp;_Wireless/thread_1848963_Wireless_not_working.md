---
title: "Wireless not working"
date: 2011-09-23
forum: Networking &amp; Wireless
---

### Post by anjaneyulu.mannam on 2011-09-23
Hi,

Wireless Adapters are not enabled and I recently installed Ubuntu 11.04 version in laptop.


Laptop model is Lenovo V460

---

### Post by PayPaul on 2011-09-23
> **anjaneyulu.mannam said:**
> Hi,

Wireless Adapters are not enabled and I recently installed Ubuntu 11.04 version in laptop.


Laptop model is Lenovo V460

Were you able to download or install the drivers for the Wireless adapter? I also committed a silly thing yesterday with my newly acquired Satellite and forgot about the radio switch on he the right side of the machine. That might seem and obvious solution and it is a windows machine. I'm still wondering if Ubuntu will actually tell me if a network adapter is uninstalled. I know I got a disconnect message when I checked the IpV6 required box while editing the Ethos0 file in Networking manager a few hours ago. I just unchecked it again and got my Internet again.

---

### Post by bkratz on 2011-09-23
> **anjaneyulu.mannam said:**
> Hi,

Wireless Adapters are not enabled and I recently installed Ubuntu 11.04 version in laptop.


Laptop model is Lenovo V460


since it is a Lenovo, it might be interesting to see the output of

rfkill list all

You may have a hard or soft block

---

