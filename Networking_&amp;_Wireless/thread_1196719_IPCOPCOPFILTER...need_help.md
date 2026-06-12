---
title: "IPCOP/COPFILTER...need help"
date: 2009-06-25
forum: Networking &amp; Wireless
---

### Post by ramon82 on 2009-06-25
IPCOP/COPFILTER...need help

Hey all!

I just created an IPCOP firewall with THREE network interfaces - Green, Orange and Red.

IP Settings set as below:

GREEN - 192.168.1.1 - Leasing DHCP 192.168.1.2-16
ORANGE - 192.168.10.1
RED - Getting IP from cable modem

Then I uploaded COPFILTER with SCP protocol and then SHH'd on the firewall and performed the install. Everything worked like a charm from the beginning till the end. Then after rebooting the COPFILTER section came up and noticed that I had to set an SMTP server to act as an email notification server. Now this is where I got stuck...

Does anybody know how I can create a mail server capable of sending/receiving from over the Internet and running on default ports 110/25. As for SMTP(out) shouldnt be a problem, but I am not sure if it can be done with POP3(in). I downloaded a freeware software which emulates as an SMTP server ([http://www.softstack.com](http://www.softstack.com)) but still cant make much sense of it.

In simple words: How can I setup a mail server? not MS exchange, something free...

Thanks!!

---

