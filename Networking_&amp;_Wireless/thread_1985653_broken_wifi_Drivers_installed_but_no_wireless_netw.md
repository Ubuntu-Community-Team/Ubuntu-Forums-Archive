---
title: "broken wifi: Drivers installed but no wireless networks to be seen!"
date: 2012-05-23
forum: Networking &amp; Wireless
---

### Post by ZomZilla on 2012-05-23
Hi,

a most strange issue has arizen: i installed 12.04 as per usual (its my third install of this and all 3 have had the broadcom chip)

for some reason when i click the network icon it says wireless disabled. when i click the enable wireless button it grays out and the other text changes to wirless disconnected.


this is odd as i have the drivers installed and can connect normally through windozer just fine. in the 2 previous ubuntu's i also had no issue and could just enable the drivers.

rfkill says: 
0: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes

and no amount of sudo rfkill unblock all can change a thing (never checked before: this could be normal)

any help/ideas?

---

