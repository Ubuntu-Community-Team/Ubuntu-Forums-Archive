---
title: "Ubuntu in Home Network"
date: 2009-09-12
forum: Networking &amp; Wireless
---

### Post by ataide.carlos on 2009-09-12
Hi all,

I'm hoping you can help me with a problem: I want to have both my laptops (Windows + Ubuntu) in my home network. I have been able to get both laptops in the same network to be able to have shared folders and stuff like that, but not every time. I don't know the reason for this, is this related to the samba configuration?

Both are using the default WORKGROUP, I can access using the LAMP stack in the Ubuntu and use FTP. I just can't find it in the network and view its shared folders.

Can anyone point me in the right direction to solve this? Thanks!
Let me know if any other info is needed.

---

### Post by zman58 on 2009-09-12
> **ataide.carlos said:**
> Hi all,

I'm hoping you can help me with a problem: I want to have both my laptops (Windows + Ubuntu) in my home network. I have been able to get both laptops in the same network to be able to have shared folders and stuff like that, but not every time. I don't know the reason for this, is this related to the samba configuration?

Both are using the default WORKGROUP, I can access using the LAMP stack in the Ubuntu and use FTP. I just can't find it in the network and view its shared folders.

Can anyone point me in the right direction to solve this? Thanks!
Let me know if any other info is needed.

I have a Linux network running at home that uses samba for CIFS network fileshares (Windows style network shares). My server is running samba server. I can easily attach to shares provided at the server (gatekeeper) using Linux or Windows. I also run a DNS server to provide logically names workstations and a network name for the server, gatekeeper. I have documented my approach and you are free to use it for reference. There are a number of issues involving determining and assigning ip addresses, providing network names, and configuring samba. You can read about it and get all of my configuration files here. This gatekeeper solution has been running for years providing great service on my network. I keep it updated with the latest Ubuntu LTS.
[http://home.roadrunner.com/~zahorec/gatekeeper.html](http://home.roadrunner.com/~zahorec/gatekeeper.html)

---

### Post by swerdna on 2009-09-12
Have a look at this primer for Samba, might help: 
[The Samba LAN Primer for Ubuntu: HowTo Set up an Ubuntu-Windows Home & Office LAN/Network]("http://ubuntu.swerdna.org/ubulanprimer.html")

If you still can't get it to work, post back here the contents of your Samba config file (smb.conf).

---

### Post by ataide.carlos on 2009-09-14
Hi all,

just wanted to thank for your help, I'm not yet sure of what the problem was, but used **system-config-samba** to get the network going. I believe its only maintained by the community.

---

