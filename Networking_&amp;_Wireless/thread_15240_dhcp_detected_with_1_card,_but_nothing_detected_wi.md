---
title: "dhcp detected with 1 card, but nothing detected with 2 ..."
date: 2005-02-13
forum: Networking &amp; Wireless
---

### Post by tameroski on 2005-02-13
hi,

i have 2 computers , 1 ubuntu , 1 xp. I want the ubuntu one to share its internet connection to the xp one.

when i have one realtek card in the ubuntu , dhcp is detected and internet works fine. So i turn it off , put trhe second card (realtek too), reboot , and then dhcp is not working, no internet , no ping ("Network is unreachable") ...

What's happening ? in the device manager , i see both eth0/eth1 with the right names , etc ...

??

---

### Post by alastair on 2005-02-13
It might be that there is a routing issue with >1 ethernet device active. I have had this - I have wired + wireless and with both active on boot I have seen the routes (including the default route) doubled up.

With the 1 card booted and everything working, show the output of :

ifconfig
route -n

Then, with the 2 cards, show the same output.

Also, show the contents of the network interface setup file :

/etc/network/interfaces

---

### Post by grj on 2005-02-13
Can you try a different card so they do not use the same driver. It has been a problem in the past trying to use multiple cards that use the same driver.

---

### Post by tameroski on 2005-02-14
i've found out what was going on :

when rebooting after installing the second card, what was  eth0 when only one card became eth1 and new card was eth0   ](*,)   .... 

so now that i've understand this, its works fine ...

thxs for the answers

---

