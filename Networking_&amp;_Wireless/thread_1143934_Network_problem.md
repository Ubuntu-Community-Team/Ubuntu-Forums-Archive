---
title: "Network problem"
date: 2009-04-30
forum: Networking &amp; Wireless
---

### Post by saintjab on 2009-04-30
I just installed ubuntu 8.10 ultimate edition 2.0 on ma laptop but am having problem connecting to the net. It was working fine with ubuntu 8.04 but the 8.10 seems to be giving problems connecting to the net with ma laptop which is using realtec rtl 8102e/8103e nic card and ma players won't play any movie file. Also i have installed the same copy on a desktop and everything is working fine. When i try to use terminal to configure, i had this error: *no buffer space available*. I will appreciate it if anyone can help me solve this problem cause i really like to use ubuntu.

---

### Post by bayvista on 2009-05-09
Networking is a real problem. I suspect that when you connected to the drive at work, it changed your setup. Post the output from *ifconfig*. Also, go to:

system/preferences/Network Config and post the values for *eth0* (I assume you are using a wired network) Check the values for:

address
netmask
gateway

Can you ping anything? Try *ping [www.google.com](www.google.com)* and post your output.

A really helpful "Howto" is [http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html](http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html)

good luck

---

