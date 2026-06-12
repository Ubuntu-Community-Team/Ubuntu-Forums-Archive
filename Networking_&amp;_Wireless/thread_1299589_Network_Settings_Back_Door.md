---
title: "Network Settings Back Door"
date: 2009-10-24
forum: Networking &amp; Wireless
---

### Post by manners2345 on 2009-10-24
I hope this the correct place to ask this???

If I use what my ISP says is a DNS server address, 192.168.1.1, which is the same as my router interface console address, my system hardly works. if I put in the DNS addresses for where I have a DNS account, system works great, until I have to shut down. When I log back on, my DNS addresses are gone, the only thing left is 192.168.1.1.

For me to log into network to change anything, I have to provide my admin password. 

How can MY ISP change my network settings with out my password??

This tells me there is a back door in Ubuntu that needs to be closed!!!!!!

How do I close this back door????????

Thank you in advance for any help!!!!!!

[email]manners2345@yahoo.com[/email]

---

### Post by t0mppa on 2009-10-24
Heh, that's a little far fetched. There's no such back door on Ubuntu. Your ISP isn't changing settings on your computer and I doubt they'd bother to do it, even if there was.

What is probably happening though is that the settings you use get overwritten by Network Manager for instance and thus returned to the default state each time you boot.

So, to know what to fix, how do you add in the DNS addresses?

---

### Post by Iowan on 2009-10-24
If you use DHCP to get an address, edit */etc/dhcp3/dhclient.conf*. Change the line: ```
#prepend domain-name-servers 127.0.0.1;
``` Uncomment it (remove the #) and add your DNS server(s).

---

### Post by slabo on 2009-10-24
Thanks for your answer. I tried this and restarted, but DNS-lookup is as slow as ever. (The DNS-entry works better from another computer here, so i figure, it's still my system that's the problem.)

---

### Post by Iowan on 2009-10-24
Check */etc/resolv.conf* to verify that it's using the DNS nameservers you set. Another option might be to try OpenDNS (208.67.222.222 208.67.220.220).

---

### Post by manners2345 on 2009-10-25
I go to the network icon, click on it, authenicate myself, hilite the NIC, go to DNS, delete 192.168.1.1, using delete button. add my 2 DNS address using add button, then close.

Sorry it took so long to answer, we have brownouts all the time. Just got power back

[email]manners2345@yahoo.com[/email]

---

### Post by manners2345 on 2009-10-25
I use open dns, I have an account.

[email]manners2345@yahoo.com[/email]

---

