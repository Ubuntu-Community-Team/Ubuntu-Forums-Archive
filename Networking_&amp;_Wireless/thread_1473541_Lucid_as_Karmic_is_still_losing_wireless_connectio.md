---
title: "Lucid as Karmic is still losing wireless connection"
date: 2010-05-05
forum: Networking &amp; Wireless
---

### Post by kukubau on 2010-05-05
Hi all

I know there are thousands of "losing wireless" posts on these forums, but I have to get it off my heart.
I have a wireless card with the rtl8187 chipset and it is randomly losing wireless connection. I am using the compat-wireless 2.6.34 rc4 drivers and it also happens with the builtin drivers that Lucid is coming with. Lucid being the latest distro I expected this will be fixed, but no it is losing connection as it did in Karmic.
It gets connected to the router, gets its ip by dhcp (and static) authenticates fine against the router, but in 5-10 seconds the connecion dies completely.
I've read so many articles on these forums and tried almost everything. I don't think manually configuring the connection will make a difference, as others had tried this, but eventually I'll do this. Otherwise, my wired connection is working just fine, plugged in the same router, also the wireless adapter is working flawlessly under windowz.

Can anyone suggest a fix for this??

Thank you.

---

### Post by Crio on 2010-05-10
You can try to limit connection speed to 11M (to 802.11b):
sudo iwconfig wlan0 rate 11M

(use your interface instead of wlan0).
Use 

sudo iwconfig wlan0 rate auto

to undo the change.

Otherwise, use you can use ndiswrapper driver.

---

