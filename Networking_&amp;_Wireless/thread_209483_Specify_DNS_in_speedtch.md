---
title: "Specify DNS in speedtch"
date: 2006-07-05
forum: Networking &amp; Wireless
---

### Post by Mickeysofine1972 on 2006-07-05
Hi

I've been using my speedtouch 330 for a while now with no problems until my ISP has asked me to try another set of DNS servers to try and fix a problem with my own domain not being reachable from my own PC ([www.michaelhibbert.co.uk](www.michaelhibbert.co.uk))

I have checked with others and they can visit the site, but when I type it in it wont respond and say cant find host.

Anyway, the point is this, how can I specify DNS servers instead of using the 'usepeerdns' command in the adsl script I created from the /usr/share/doc/ppp/examples/peers-pppoa file in the howto?

I need to be able to set them to test if they work as the dns does not get set at the IPs I want on connection.

HELP! 

Mike

---

### Post by Mickeysofine1972 on 2006-07-20
Well I fixed it!

All you have to do is edit /etc/resolv.conf and there should be the ip of your already connect DNSs, then you just change those IPs to the ones you wnat and reboot.

Jobs a good un!

Mike

---

