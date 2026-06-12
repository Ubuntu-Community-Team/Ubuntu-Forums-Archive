---
title: "cannot connect xp thru wireless bridge wired to eth0"
date: 2010-01-23
forum: Networking &amp; Wireless
---

### Post by dabernard on 2010-01-23
I am trying Ubuntu on a trial basis to see if I think I could use it in place of Windows. One of the things I can do in Windows is connect my XP laptop thru a wireless access point which is connected by ethernet cable to my desktop, which is set to share its internet connection. The desktop connects to the internet by dialup. For my WAP, I use a Buffalo Tech Air Station model WHR-HP-G54 set to bridge mode with a crossover cable between one of the Air Station LAN ports and the desktop ethernet port.

Picture would be something like this
xp wireless adaptor -- WAP -- eth0 -- ppp0 -- internet

Note: there is no router, just a WAP set to bridge mode.

In Windows, the ethernet connection is set with a fixed IP address of 192.168.0.1 and a subnet of 255.255.255.0. I have set the auto eth0 connection to manual with the same settings in Network Manager. I thought before I tried to see if I could get Internet Connection Sharing to work with the Ubuntu desktop, I would try to confirm that I can connect my XP to the Ubuntu desktop over the same WAP. I have installed dhcp3-server and even  (out of desperation) tried creating a bridge between the access point  and eth0 but am unable to connect to the xp laptop. Nothing works. The xp laptop  will not acquire an ip address from the Ubuntu desktop wired to the WAP.

Has anyone been able to successfully set up a similar situation? If so, got any advice? I am using Ubuntu 9.10. I'm not a networking pro, so I want to keep it pretty basic. Otherwise, I might just have to stick to Windows. Can anyone help?

---

