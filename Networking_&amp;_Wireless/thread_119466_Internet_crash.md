---
title: "Internet crash"
date: 2006-01-19
forum: Networking &amp; Wireless
---

### Post by shellofinsanity on 2006-01-19
I'm new to linux, having just switched from windows XP. My problem is when I connect to my wireless network/DSL modem it forces it to disconnect from the internet. The modem is a 2wire 1000HG. Below are the settings I added to the network config.

IP Address
192.168.1.65
Subnet
255.255.255.0
DeFault Gateway
192.168.1.254
DNS
192.168.1.254
Hostname
Phil.gateway.2wrie.net

Are these settings correct. I know the Routers internal IP is 192.168.1.254.

---

### Post by mips on 2006-01-19
[http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643)

Please be a bit more specific about your problem, network topology etc.

---

### Post by stream303 on 2006-01-20
> 
DNS
192.168.1.254

I may be wrong, but I've got a strange feeling that you probably don't want dhcp to pick up the DNS of your router, but you want your isp's dns addresses instead.

If you can get hold of those, either from your existing XP machine's configuration setup, or from your isp's docs, you might be able to edit your network configuration -- assuming just dhcp, adsl router, ethernet connection etc...

Kind of bumping around in the dark here, but it's a start....

---

