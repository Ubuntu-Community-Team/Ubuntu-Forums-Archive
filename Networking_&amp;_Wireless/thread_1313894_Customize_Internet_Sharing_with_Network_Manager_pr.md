---
title: "Customize Internet Sharing with Network Manager problem"
date: 2009-11-04
forum: Networking &amp; Wireless
---

### Post by sepent on 2009-11-04
Hi,

I installed ubuntu karmic recently and I want to setup a NAT on my machine. So I used "shared to other computers" in Network Manager and everything works fine.

Now my local IP address is 10.42.43.1 and the DHCP server IP range is 10.42.43/24 or maybe 10.42/16. I prefer 192.168.0/24 range, but I couldn't find any where to change this range. Should I create a custom /etc/dnsmasq.conf file or is there any any other solution?

---

### Post by sepent on 2009-11-04
Any solution?

---

### Post by redmk2 on 2009-11-04
> **sepent said:**
> Hi,

I installed ubuntu karmic recently and I want to setup a NAT on my machine. So I used "shared to other computers" in Network Manager and everything works fine.

Now my local IP address is 10.42.43.1 and the DHCP server IP range is 10.42.43/24 or maybe 10.42/16. I prefer 192.168.0/24 range, but I couldn't find any where to change this range. Should I create a custom /etc/dnsmasq.conf file or is there any any other solution?

At startup DNSMasq reads /etc/dnsmasq.conf.  You can set all the parameters there.  See [_**[COLOR="DarkSlateGray"]here[/COLOR]**_]("http://www.thekelleys.org.uk/dnsmasq/docs/dnsmasq-man.html").

I'm curious, what do you feel is the difference between 192.168.0.0/24 and 10.0.0.0/24?  For that matter what is the difference between differing /16 network numbering schemes?  Other than the amount of IP addresses in each range (/16 vs /24, I believe that there is no functional difference between the ranges (e.g 10.0.0.0/16 and 192.168.0.0/16 **or** 10.0.0.0/24 and 192.168.0.0/24).

Most network engineers use CIDR rather than IP address classes now.  See [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://www.cisco.com/en/US/tech/tk365/technologies_tech_note09186a0080093f33.shtml").

Edit: proper forum etiquette requires you to wait 24 hours to "bump" your question.  :-)

---

