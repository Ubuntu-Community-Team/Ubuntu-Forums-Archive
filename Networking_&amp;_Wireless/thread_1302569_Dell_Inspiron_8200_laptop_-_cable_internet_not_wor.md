---
title: "Dell Inspiron 8200 laptop - cable internet not working!"
date: 2009-10-27
forum: Networking &amp; Wireless
---

### Post by kvarley on 2009-10-27
So I installed Karmic on this old laptop and it's works a treat apart from the internet. I installed the os without having an ethernet cable plugged in.

Now auto eth0 wont connect, any ideas of what I can do?

---

### Post by Iowan on 2009-10-27
I haven't tried Karmic yet - so any advice is from prior versions...
Check **ifconfig -a**. It probably won't have IP address, but note the MAC address. You should be able to right-click Network Manager and edit "Auto eth0" connection (you'll need MAC address). Enable "Connect automatically" and restart/reboot. (I prefer to reboot to insure Network Manager and the other networking components get properly synchronized.)

---

