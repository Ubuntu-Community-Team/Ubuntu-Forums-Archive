---
title: "Can't find wireless networks"
date: 2009-09-06
forum: Networking &amp; Wireless
---

### Post by Cstryon on 2009-09-06
I think I got my card working, it is no longer disabled. But I can't see any wireless networks. Someone in the #ubuntu chat told me to run sudo iwlist wlan0 scan
I did that in the terminal and got this error

wlan0     Failed to read scan data : Resource temporarily unavailable

When I told that to the guy in the chat he said something about running a scan in the interface? He then told me I should familiarize myself with ubuntu. Well I'm not so sure what I need to know. My problem is that I can't find wireless networks. Can anyone help me? What is the proper way to run this scan?

---

### Post by Hosmion on 2009-09-06
Do you have wireless networks enabled?  Go to the icon for the wireless, make sure the Enable Wireless is checked..

Or, manually configure your wireless internet by :

**Right Clicking the Wireless Icon** > **Edit Connections** > +**Add**.. > **Configure the connection**

---

### Post by comorbid on 2009-11-04
I think the OP is unaware of the actual SSID, and was referring to the functionality present in Windows/MacOS which allows you to see the names of available wireless networks in the immediate area.

That command should have done the trick, so I'd suspect the wireless adapter still might not be functioning if there are available networks in the area.

EDIT: Sorry for the necro, didn't check the actual month in the date.

---

