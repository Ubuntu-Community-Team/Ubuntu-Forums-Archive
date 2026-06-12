---
title: "Unable to browse internet although connected"
date: 2011-03-28
forum: Networking &amp; Wireless
---

### Post by mcci6 on 2011-03-28
Hi,

I've just installed Ubuntu 10.04 on my laptop, replacing Ubuntu 8.10 which I was previously using. The installation went smoothly, but I seem to be having some internet problems:

- I am unable to browse the internet in Firefox even though my internet connection is working.
- I am able to log into my Google Talk account using Empathy and can see online users, so I know I am connected to the internet.
- I have tried both wireless and wired connections.
- I have tried pinging using Network Tools and they ping websites successfully with no dropped packets.
- I tried to get updates but I get error messages.
- I have another laptop (Windows XP) connecting to the internet using the wireless network at home and it works fine.
- From reading some forums, I've tried disabling IPv6 in Firefox using about:config but it made no difference.
- From reading some forums, I've tried under to edit the internet connection for IPv4 to Automatic (DHCP) addresses only and putting the DNS server of my ISP below, but again no success.

I don't really know what I'm doing, just trying out some suggestions from forums, so before I muck it all up and mess it further, could someone help me with some guidance about what to do to be able to browse the internet again on Ubuntu 10.04?

Thanks so much for your help!
mcci6

---

### Post by mcci6 on 2011-03-31
Anyone able to help with my query?

Without the ability to use the internet on my Ubuntu laptop, I'm not able to use that laptop, and have to revert to a Windows laptop. Would really appreciate any help with my problem.

Thanks!

---

### Post by patryk77 on 2011-04-01
What is the exact error message firefox is giving you?

Can you ping addresses with a domain name ([www.google.com](www.google.com)) or just an IP address?

Can you open a website using an IP address? [http://74.125.159.147](http://74.125.159.147)

What are the error messages you get when you try to get updates?

Try them from the terminal, it will be easier to copy/paste:
sudo apt-get update

Also, make sure you have no proxy set; System / Preferences / Network Proxy

---

