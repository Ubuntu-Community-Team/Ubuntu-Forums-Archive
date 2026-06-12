---
title: "Changing the DNS in Network Manager - strange situation?"
date: 2010-10-19
forum: Networking &amp; Wireless
---

### Post by zozza on 2010-10-19
Hello,

I am having some problems changing my DNS.  Let me explain.  

I am on my University network.  I am using Network Manager.  The default setting is Automatic (DHCP) which, AIUI, means my IP and DNS is set automatically.  If I change it to Automatic (DHCP) addresses only then I should be able to set my DNS.  However, when I enter the OpenDNS server, although /etc/resolv.conf does change, I connect to my wireless network but have no ability to send / receive any data.  Removing these settings and returning to Automatic (DHCP) enables me to send / receive traffic again.  

However, I can use a VPN which does change the DNS settings.  In Network Manager the setting is Automatic (VPN).  My /etc/resolv.conf changes to:

domain my domain.ac.uk
search my.domain.ac.uk
nameserver vpn dns
nameserver vpn dns
nameserver university dns

And I can connect and send / receive as normal.  

I can understand that my University has blocked the ability to change the DNS.  What I do not understand is how I can change the DNS with a VPN but not manually?

Any ideas?  Thanks.

---

### Post by M!K3_$ on 2010-10-19
> **zozza said:**
> 
I can understand that my University has blocked the ability to change the DNS.  What I do not understand is how I can change the DNS with a VPN but not manually?

You could technically give yourself a static IP(just try the last DHCP address your machine was given).

Then match up your subnet mask and your gateway; then change your DNS to what ever you want.

If you want, google has a DNS on 8.8.8.8, if you want to try that.

---

### Post by zozza on 2010-10-20
> ou could technically give yourself a static IP(just try the last DHCP address your machine was given).

Then match up your subnet mask and your gateway; then change your DNS to what ever you want.

If you want, google has a DNS on 8.8.8.8, if you want to try that. 	

I did this and, as expected, although I connect to the network I then cannot send / receive any traffic.  

I don't understand how I cannot change the DNS but a VPN can change the DNS?

Also, in the IPv4 settings of the Network Manager there is "DNS settings" and "Search domains" - what is the difference; how can the domains be used to resolve host names?

Thanks.

---

### Post by M!K3_$ on 2010-10-20
To be honest, I never use Search Domains and because of this I'm unfamilliar with them. They are a bit of an "extra".

When you connect to something via VPN, a tunnel interface is created on your machine. That interface has an IP address, subnetmask, default gateway, and DNS IPs just like a regular interface. The only difference is your IP address is given by the VPN server/router and it (usually) acts as the default gateway/DNS.

I'm not sure if that is what you meant by the "VPN can change the DNS"

---

