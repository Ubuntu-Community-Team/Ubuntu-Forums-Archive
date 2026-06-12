---
title: "virtual box internet connection through mobile gprs"
date: 2011-05-07
forum: Networking &amp; Wireless
---

### Post by paresh-ubun2 on 2011-05-07
Hi,

I access internet on windowsxp through mobile gprs connection.

I want to access the internet from ubuntu installed in virtual box.

Host OS: WindowsXP
Guest OS: Ubuntu 10.04.LTS
Virtual Box: v4.0.4
Mobile connected to PC through USB.

With Virtual box settings of NAT and BRIDGE internet is not working.

Can you please help me in setting up the internet access through virtualbox.

Thanks
Paresh


By default VirtualBox Settings for Netwoek Adapter uses NAT. I changed to BRIDGED and back to NAT. and internet access has started working now.

---

