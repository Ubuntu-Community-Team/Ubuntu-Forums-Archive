---
title: "wireless router setup"
date: 2010-06-05
forum: Networking &amp; Wireless
---

### Post by tonymoloney on 2010-06-05
Due to my geographical location, I receive my Internet signal via a Wireless Application Point (WAP) attached to a 20Db antenna. This signal is then routed to my computers via a wireless router which is attached to the WAP by its RJ45 cable. Each of my 4 computers are then hardwired to the router and my laptop is attached via its wireless function.

This setup has been working fine for the last two years, but recently my router has developed a problem and I have replaced it with a new one. I am now having problems getting the new router to talk to the WAP.

My  network administrator requires our hardware to have static addresses, but the computers connected to the router have always worked with DHCP.

This is the setup that I am trying to get functioning:

WAP: IP address, 172.16.2.39, Sub-net mask, 255.255.252.0, gateway 172.16.3.254
Router:  IP address 172.16.1.39, Sub-net mask, 255.255.0.0, gateway 172.16.3.254
Computers: IP addresses DHCP


I can ping 172.16.1.39 from any computer, but cannot ping 172.16.2.39
The only options I have for the router's sub-net mask are either 255.255.255.0 or 255.255.0.0 
I have tried both these options without success.
Three other people on our network have similar setups which work for them.
Any ideas, anyone?

---

