---
title: "WMP600N / Ralink 2860 in Ubuntu 9.10 / solutions?"
date: 2009-12-13
forum: Networking &amp; Wireless
---

### Post by ariel on 2009-12-13
Anyone succeeded in using a WMP600N / Ralink 2860 in Wireless-N mode? Or was even able to use this card in Wireless-G mode with no drops?

I found the included rt2860sta driver to be very unstable, and on top of that it has some interaction problem with NetworkManager - the kernel log ring buffer fills up with weird messages coming from the driver whenever NM is running. On top of that, the connection drops every couple of hours. 

Ralink provides a newer driver source, however it does not compile under kernel 2.6.31. I couldn't find any working patch that actually makes it work in Karmic. Wrote to ralink, no answer.

There is Serialmonkey / RT2800PCI. The one that comes with Karmic is not even able to recognize the card. I installed a nightly of compat-wireless for the latest rt2800pci code. It does recognize the card (I can see it with iwconfig) and it can even scan networks and seems to associate in Wireless-G however it fails to receive or send any packet so in reality, it doesn't work; I could find no reports in google of anyone actually using this driver for any practical purpose.

My temporary solution is to use the old Karmic rt2800sta, remove NM, statically configure the interface via /etc/network/interfaces and ralink's /etc/Wireless/RT2860STA/RT2860STA.dat. This gives me wireless-G, no dmesg errors but connection lasts only for 24h or so. 

Anyone came up with a working solution? patch for the latest rt2860sta so that it compiles and works in ubuntu? or same magic to make rt2800pci work?

Ideally I need to connect in Wireless-N with WPA, but no encryption in Wireless-N would work as well. Alternatively, I'm OK with rock solid Wireless-G with WEP. I can get none of this currently.

Thanks[IMG]chrome://dictionarytip/skin/book.png[/IMG]

---

### Post by carcar1 on 2009-12-13
We seriously need to get the devs to my house cause I am like the only one that can get this card to run natively on 9.04 and 9.10 flawlessly.  I am using the encore version of this card and it works great!  Haven't tried n mode only have a g router with verizon.

---

### Post by ariel on 2009-12-13
> **carcar1 said:**
> We seriously need to get the devs to my house cause I am like the only one that can get this card to run natively on 9.04 and 9.10 flawlessly.  I am using the encore version of this card and it works great!  Haven't tried n mode only have a g router with verizon.

which driver are you using? stock rt2860sta with network manager?
thxs

---

