---
title: "local dns server  should check hosts file, or similar"
date: 2013-02-03
forum: Networking &amp; Wireless
---

### Post by ralph1973 on 2013-02-03
Hello,
I have running a mailserver. When I am in my house, I want hosts on my (wifi) network connect to the local ip adress of my server instead of the internet address. So dns should reply with the local ip. 
I did set up a local dns server (bind9), and when wifi clients request my mailserver address, it replies with the public ip. How can I have my dns server reply with the LOCAL mailserver ip instead of the public one?

Kind regards,
Ralph Willemsen
Arnhem, Netherlands

---

### Post by TheFu on 2013-02-03
> **ralph1973 said:**
> Hello,
I have running a mailserver. When I am in my house, I want hosts on my (wifi) network connect to the local ip adress of my server instead of the internet address. So dns should reply with the local ip. 
I did set up a local dns server (bind9), and when wifi clients request my mailserver address, it replies with the public ip. How can I have my dns server reply with the LOCAL mailserver ip instead of the public one?

Do your wifi clients have the correct DNS server listed first in their  /etc/resolv.conf?  Order matters.  Is your local DNS server "authoritative?"

Running a local bind on a PC might be considered overkill for stuff like this.  Any router that supports dd-wrt or similar firmwares can usually run a DNS server easily, provide static IP reservations for portable devices via DHCP and give a central place to manage host names for every machine on the network.  There are hundreds of how-to articles on the internet. [http://www.dd-wrt.com/wiki/index.php/DNSMasq_-_DNS_for_your_local_network_-_HOWTO](http://www.dd-wrt.com/wiki/index.php/DNSMasq_-_DNS_for_your_local_network_-_HOWTO) is one.

Regardless, also check your /etc/nsswitch.conf on the machine running bind.  Bind is one of the few programs that I needed to buy a book to understand and after reading just 6 pages in the O'Reilly book, I was able to solve my issues. At the time. I thought, it was the best book ever written to be able to solve my complex issues so quickly.

Based on your question, I suspect that you've already checked the things I've said.  Do you have any other diagnostic data to share?

---

