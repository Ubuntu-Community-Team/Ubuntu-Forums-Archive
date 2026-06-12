---
title: "Motorola Surfboard 5100 stoped working after kernel upgrade"
date: 2009-07-31
forum: Networking &amp; Wireless
---

### Post by fobos3 on 2009-07-31
Hi,

I have Motorola surfboard 5100 modem connected via a USB to my ubuntu jaunty box. After a kernel ubdate and a restart I cannot connect to the internet any more. The IP, broadcast, netmask, DNS, device driver are the same. I have a dual-boot with win XP, which my brother uses, and I had internet there. Then I decided to reinstall the drivers for windows and as a result I don't have internet in windows as well. I've tried to boot from the older kernels but the story is the same. Finally, I've booted from an ubuntu USB live and I have a perfect connection (I am currently writing from the live boot).

Any input will be appreciated, 'cause I'm currently bemused.

P.S.
What is interesting is that the ubuntu update caused problems in windows.

Edit
Everything is fixed. For some reason ubuntu decided to change the rules in iptables from ACCEPT to DROP, which happens after each reboot. Any idea how to save iptables so it is not affected after reboot. I run the following in order to enable my internet connection:
root@david-desktop:/home/david# iptables -P INPUT ACCEPT
root@david-desktop:/home/david# iptables -P FORWARD ACCEPT
root@david-desktop:/home/david# iptables -P OUTPUT ACCEPT

---

