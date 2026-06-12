---
title: "SSH/ICS Client unable to connect to SSH/ICS Server"
date: 2012-04-25
forum: Networking &amp; Wireless
---

### Post by TheRavager on 2012-04-25
Here's my setup:

                                Laptop (ubuntu 11.10 hostname home)
Internet  --> (wireless) eth1 (dynamic dhcp) --> eth0 (10.0.0.1)(ICS/dhcp)  --> LAN port 1 of wired/wireless router (dhcp off) --> wired and  wireless clients

Internet is working great for wired/wireless  clients. I am desiring now to make a SSH connection @home . In this case  a client wired to LAN port 2 of said router.

SSH server is listening on 0.0.0.0:22 and was able to login via localhost

From client I have tried

```
ssh root@10.0.0.1
``````
ssh root@home
```I further try, using the IP address assigned

```
ssh root@192.168.1.9
```all attempts to connect time out. 

my concerns:

1. Are these the correct commands to make a ssh connection
2. doubting the router is port blocking on otherwise default settings (dhcp was turned off) but worth further investigation.
3.Although  @home is listening on 0.0.0.0 port 22 could it be unable to respond as  eth0 is dedicated ICS/DHCP server and eth1 is dynamically receiving  internet?

   I may have an extra PCMIA ethernet card laying  around to make a 2nd connection to said router for lan port 3. Perhaps I  need a dedicated (eth2 for ssh server?) It just seems redundant though.  I should be able to atleast connect via the wifi addy shouldn't I? Except  differing subnets? Do I then need to create a virtual bridge to make my  way back in around although via ICS? If that makes sense.

---

