---
title: "ubuntu 10.04 conectivity eth0 issues"
date: 2010-11-29
forum: Networking &amp; Wireless
---

### Post by tru infini on 2010-11-29
Yesterday the strangest thing happened, I dropped my wireless keyboard and when i went to catch it, I hit one of the power management buttons and my screen went dark. for whatever reason, If my computer goes into hibernate or sleep mode, the only way to get it out is a hard reset. This happened and when I started my computer up again, my firefox started up in offline mode. long story short, I got my internet working by using the four lines:
sudo ifconfig eth0 down
sudo dhclient -r eth0
sudo ifconfig eth0 up
sudo dhclient eth0

that gets my internet working again but if i shutdown or reboot then I have to type those commands into the terminal again. I managed to fix the offline mode by installing an extension that tells it to always start in online mode no matter what. how do i fix this?:icon_frown:

---

