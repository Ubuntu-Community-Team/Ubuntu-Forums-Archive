---
title: "card upgrade"
date: 2010-10-26
forum: Networking &amp; Wireless
---

### Post by gavfranc on 2010-10-26
Hi all,

I have successfully installed edubuntu ltsp and got 15 clients running from the server. I had to upgrade my network card to a gigabit one and now system has appended the card to eth2 and dhcp server not seeing card.

Does anybody know how to reconfigure the LTSP server to either use eth2 or to rename the new card to eth1 as it was before. I do not want to go back to the 10/100 card as its too slow.

Thanks

---

### Post by chili555 on 2010-10-26
Please see /etc/udev/rules.d/70-persistent-net.rules. You can amend it to remove the lines applicable to the old card and amend the lines applicable to the new card to change eth2 to eth1. You can identify which is which by MAC address.

Reboot and you'll be all set. If you are reluctant to restart, you might try restarting udev.

If you need further guidance, please post back.

---

