---
title: "OpenVPN versus Network Manager"
date: 2009-08-27
forum: Networking &amp; Wireless
---

### Post by mykrob on 2009-08-27
Having a problem with VPN and Network Manager. I have an OpenVPN server up and running at my church, and it works just fine. I have successfully connected to it multiple times from Windows machines using the OpenVPN client software.

I have imported my keys into NetworkManager, which claims that I have successfully connected to the VPN, however I am unable to access any remote network resources or browse the internet while it "claims" i'm connected. Within just a few minutes, the VPN is terminated. Basically, it seems as though the connection is not being completed for whatever reason, and I feel the issue lies in NetworkManager since I can connect just fine from another OS without any issues whatsoever and without being dropped from the connection.

In short, I need some help getting Network Manager to work, or whatever I  need to do in Ubuntu (gnome) to successfully connect to my OpenVPN server.

Thanks in advance for any help anyone can give.
-myk

---

### Post by mykrob on 2009-08-28
Still no luck. I know that people are successfully using VPN connections in Linux.. what the heck am i missing here??

---

### Post by mykrob on 2009-08-28
Change of plans, I got the VPN working now. I copied my files (certificates and .conf) to /etc/openvpn and then imported teh .conf file into NetworkManager. I am now able to browse remote network shares. The only problem now is while connected via VPN, I am unable to browse the internet. 

Any ideas?

Thanks,
-myk

---

### Post by mykrob on 2009-08-30
bump....

---

### Post by mykrob on 2009-08-30
Got it:

Go to IP4 -> Advanced -> Routes and enable the "Use this connection only for resources on its network" option.

---

