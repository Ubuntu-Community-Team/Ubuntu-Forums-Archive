---
title: "IP Conflict"
date: 2013-05-03
forum: Networking &amp; Wireless
---

### Post by Vishal Agarwal on 2013-05-03
Hi,
Kindly advise how can I search problematic client machines those are creating IP conflict, at my network, while all the computers are configured with static IP's.

---

### Post by TheFu on 2013-05-03
The best answer really depends on your network.  I've worked places where every RJ45 port could be disabled remotely. Disabling an offending port would be the easiest solution.  Hopefully whoever did this on your network didn't select an important IP, like that of the router.  With managed switches, you can power off the switch port remotely too. That will bring the end user who did this CRIME asking for help.

I would use **nmap** with OS identification as a starting point. Then I'd probably use **arp** and lookup on the internet which vendor made the network card. That might help determine the specific device.

Subnetting different clients to different subnets can help to prevent this sort of thing. Servers, phones, desktops and wifi devices all on different subnets.  Using DHCP reservations can help put portable devices on specific IPs when those devices are on your network, while leaving them as regular DHCP clients on different networks.

If you can login to each machine, the **ifconfig** command will display the MAC and the IP.

Perhaps someone else will have a better answer.

---

### Post by prodigy_ on 2013-05-03
> **TheFu said:**
> I'd probably use **arp**
Indeed. [http://www.cyberciti.biz/faq/linux-duplicate-address-detection-with-arping/](http://www.cyberciti.biz/faq/linux-duplicate-address-detection-with-arping/)

---

