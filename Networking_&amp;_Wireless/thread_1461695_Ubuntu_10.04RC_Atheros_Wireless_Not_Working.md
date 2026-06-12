---
title: "Ubuntu 10.04RC Atheros Wireless Not Working"
date: 2010-04-24
forum: Networking &amp; Wireless
---

### Post by baloo56 on 2010-04-24
Does Ubuntu 10.04RC support Atheros AR2427 wireless card out of the box? I ran 10.04RC Netbook Live on my new Asus Eee 1001P Netbook today and it looks very impressive indeed. However, I could not get Ubuntu 10.04 to even see the Etheros AR2427 card (iwconfig). Am I doing something wrong or is there no driver to support the card?
If no driver what are my options to get it working under 10.04 as I do not want to use Windows on my netbook...many thanks.

---

### Post by jerome1232 on 2010-04-24
Madwifi works with alot of Atheros drivers, but it depends on HAL and I believe 10.04 is doing away with HAL.


There is ath5k and ath9k. I don't have an atheros chipset so I have zero experience or know how with these drivers, you can check them out on the madwifi website.

[http://madwifi-project.org/](http://madwifi-project.org/)

Hope that at least gets you pointed in the right direction.


edit: I see ath9k says it supports your chipset, doesn't work with n but does work with b/g.

---

### Post by baloo56 on 2010-04-25
Hi Jerome1232
Thank you for the reply. I checked out the link you gave me but it looks like the ath9k supports only 802.11n chipsets not B or G...pity.
Copied this statement from the link site: "**ath9k is the youngest of the three drivers. Initial development was done by Atheros, who then released the complete source code to the community. ath9k supports all currently available 802.11n chipsets from Atheros**". My Atheros wireless card is B/G only...not N.
I am hoping that the final release of Ubuntu 10.04 on April 29th 2010 will include the correct driver to solve my problem. If not, I am sure someone will come up with a fix.

---

### Post by jerome1232 on 2010-04-26
Your misreading that, on the link it provides it goes on to state that the driver supports 802.11abg, and 802.11n.

---

### Post by baloo56 on 2010-04-26
Hi Jerome1232,
You are correct. I didn't look far enough. Thank you.

---

