---
title: "Wireless Works, but can't see my network."
date: 2009-10-27
forum: Networking &amp; Wireless
---

### Post by zeroo on 2009-10-27
When I go to connect to a wireless network, ubuntu 9.10 provides me with about 20 networks from around my neighborhood. 
The problem is, I can't see my router.  I read that only channels 1-10 work so I turned off auto channel and changed it to channel 3.  Still can't see it.
I have 3 other computers in my house connected to the network.
Any ideas why I can't see my router?

any help would be greatly appreciated.
Thanks

---

### Post by bkratz on 2009-10-27
> **zeroo said:**
> When I go to connect to a wireless network, ubuntu 9.10 provides me with about 20 networks from around my neighborhood. 
The problem is, I can't see my router.  I read that only channels 1-10 work so I turned off auto channel and changed it to channel 3.  Still can't see it.
I have 3 other computers in my house connected to the network.
Any ideas why I can't see my router?

any help would be greatly appreciated.
Thanks

Is your wireless hidden?  If you feel comfortable with the terminal execute a


iwlist scan     ----to see all available networks, hopefully your s too.

---

### Post by zeroo on 2009-10-27
No my network isn't hidden.

And when I type in iwlist scan is says that the interface does not support scanning.

---

### Post by bkratz on 2009-10-27
> **zeroo said:**
> No my network isn't hidden.

And when I type in iwlist scan is says that the interface does not support scanning.


sorry, it should have been sudo iwlist scan

Do you know what wireless card you have?  If not, either do a

lspci or lsusb depending on whether it is internal or a usb dongle,

that should help us.

---

### Post by zeroo on 2009-10-27
With iwlist scan, my network does not come up, yet other ones do. 
And I have Hawking HWDN1. 
A few months back I was using 9.04 with the same setup without any problems.  I went to windows then came to 9.10 and now it can't see my wireless network.
Is there some router setting that would make this happen?

---

### Post by jltrammell on 2009-11-01
I'm having the same problem and have tried everything.  Did you get this figured out.  I have a Linksys WUSB600N card and a Linksys WRT610N router.  I can see all my neighbours routers but not mine.  SSID is broadcasting fine.  Just can't see it on Ubuntu 9.10

---

