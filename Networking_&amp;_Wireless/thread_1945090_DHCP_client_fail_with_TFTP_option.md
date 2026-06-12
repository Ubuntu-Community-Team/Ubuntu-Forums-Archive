---
title: "DHCP client fail with TFTP option"
date: 2012-03-22
forum: Networking &amp; Wireless
---

### Post by hugolia on 2012-03-22
Hi everybody!
I am running into problem with the DHCP client on my Ubuntu 11.04 notebook.
It was working fine with a DCHP server running on pfSense. But lately we instaled a IP-PBX that required TFTP option for the IP-phones auto configuration. We set the TFTP-server option on the DHCP server and all went well till I reboot my notebook.

My notebook set the TFTP server address as gateway and DNS from the DHCP client.
Others machines in the network (Windows machines) get the DNS and gateway right, only the Ubuntu desktops got this problem.

Can anyone help me to solve this problem? or guide to diagnose it.

Thanks
Hugo

---

