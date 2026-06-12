---
title: "Wireless adapter picks up signals but cannot connect"
date: 2006-06-16
forum: Networking &amp; Wireless
---

### Post by Hyphessobrycon on 2006-06-16
I have a [2wire usb wireless adapter]("http://www.2wire.com/?p=117") that I think I got to function with ndiswrapper. It is picking signals from my wireless network, but when I try to connect it to my router, something goes wrong. I select the correct ESSID from the Network utility, input the WEP key, and set the IP field to DHCP. I have also tried configuring it with a static IP, and it still doesn't seem to work. From the Terminal, I have tried deactivating it with ifdown and then reactivating it with ifup. It waits awhile, and then says that no IP was assigned. Is there anything that I might be doing wrong? Should I do anything else?

---

### Post by tturrisi on 2006-06-16
will it connect w/out wep enabled in the router?

---

### Post by noname101 on 2006-06-17
What does iwconfig say after you try to connect?

---

### Post by Hyphessobrycon on 2006-06-17
I tried removing the WEP key, and it connected to my network. Thanks for the help.

---

### Post by tturrisi on 2006-06-17
OK, now we know the adapter & connection work.  Now, to use WEP try using dashes inbetween the characters in the Network config window:
xx-xx-xx-xx-xx
(I have seen this done as a workaround and was successful for some.  May or may not work for you.  If no joy then disable wep in router again until a fix is arrived at.

---

