---
title: "3G Internet Connection Sharing"
date: 2011-01-24
forum: Networking &amp; Wireless
---

### Post by psyaneyed on 2011-01-24
I am trying to get my system to sustain a shared connection via a 3G WWAN Card.  Here is my setup:

Netgear Router WGR614
Not set to act as DHCP Router, but is set to use as WAP

Sierra Wireless 3G USB Adapter (59 8 I believe) -- Drivers built in to Ubuntu
Provider - Thumb Cellular (Small MI based provider)

I am able to get the sharing to  work via Windows, but not on Ubuntu.  The connection works fine until someone else tries to use it.  The weird thing is it will work for about 5 minutes, then the network will stay disconnected and refuse to connect until rebooted.  The Mobile Broadband Connection connection in the network manager does not allow me to set it up for other users to utilize, but I have shared the eth0 connection.

I'm not sure what the particulars are with ICS in Ubuntu, but I'm not sure why it will only die when others connect after some time working just fine.  I was thinking its a possible routing issue, but I can't be sure.  Authentication is done via PPP (Method unsure)

---

