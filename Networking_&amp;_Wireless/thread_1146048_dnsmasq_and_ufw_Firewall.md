---
title: "dnsmasq and ufw Firewall"
date: 2009-05-02
forum: Networking &amp; Wireless
---

### Post by j_a_n on 2009-05-02
I'm usigin dnsmasq as DHCP und DNS-Server for my network. 

After enabling the ufw-firewall dnsmasq does not work any longer.

# ufw app list
does not list a pre-configured profile for the dnsmasq-server.

Does anyone has such a pre-configured profile file?

---

### Post by dpward on 2009-05-23
I had the same issue, and found commands to add the appropriate firewall rules to allow DNSMasq to work:

# allow serving DHCP requests
sudo ufw allow from any port 68 to any port 67 proto udp

# allow serving DNS requests
sudo ufw allow 53

# apply changes
sudo ufw disable
sudo ufw enable

---

