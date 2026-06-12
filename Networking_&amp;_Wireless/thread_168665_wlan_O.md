---
title: "wlan O"
date: 2006-04-30
forum: Networking &amp; Wireless
---

### Post by majkmil on 2006-04-30
I have a Linksys usb wireless adapter that works out of the box in breezy. My problem is when I startup my computer Ubuntu activates wlan O AND etho O, but I do not have a wired connection only wireless. To get the wlan O to work I have to deactivate both wlanO and ethO and then activate wlan O. Why does ubuntu try to activate etho O when there is no connection. Can I configure breezy to use my wireless card during boot? Boot screen always stops for a while trying to sycrinize with ubuntu clock. Thanks

---

### Post by majkmil on 2006-05-01
Problem solved, atleast for now. I had to put in my WEP key. I am pretty sure that it gave me the problem before when I did not have wep enabled at the router. Anyway it recognized the wireless usb adapter at boot and seems to be working. How do I deactivate ethO at boot so I only have wireless at startup? Thanks

---

### Post by sailor2001 on 2006-05-01
syn clock only works if you have already a conection. hurry it along on boot up with "ctrl+c"

---

