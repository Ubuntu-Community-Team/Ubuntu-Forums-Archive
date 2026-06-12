---
title: "Draytek Vigor 2710n VPN and DynDns"
date: 2011-03-04
forum: Networking &amp; Wireless
---

### Post by BurtaN on 2011-03-04
Hi,

I'm trying to create a VPN-Tunnel so that I can access my home-LAN via internet. I've got a Draytek Vigor 2710n Router and a T-Online Internet connection. 
For the reason, that my WAN IP changes about every 24h, I've registered at [www.dyndns.org](www.dyndns.org). When I've understood dyndns correctly, my router tells my ddns host, which WAN IP it has and my VPN clients requests this IP from the ddns host? What ever, I activated DynDns and created an account. Provider is dyndns.org, type is dynamic. Domain name is XXXX.dyndns.org. Username and password is set as given by [www.dyndns.org](www.dyndns.org). When connecting and checking the log, it seems to work as the result is:

"DDNS is updating
A= "username", H="address given by dyndns.org", U=1
Connecting to the DDNS server
Return Code= good (IP Adress)
Updated successfully."

Anyway, I'd like to start with PPTP, because it seems to be the easiest and most compatible solution (although not the savest).

I'll begin with my router's setup.
I've activated PPTP VPN Service. Dial-In Authentication is PAP or CHAP. Dial-In Encryption is Optional-MPPE. Mutual Authentication is off. Next is the Dial-In Users setting. I've created an account. Timeout is 0. Dial-In Type is PPTP. Username and password is configured. That should be all concerning the router.

Now, I'm trying Ubuntu 10.10 to create the VPN tunnel. 
Gateway is XXXX.dyndns.org Username and password as setup in the router's menu. Authentication method is MSCHAP and MSCHAPv2. Use Point-to-Point encryptions is activated. Security is Default and Allow stateful encryptions is activated as well. Next 3 checkboxes are unchecked and Send PPP echo packets is activated.

Well, it doesn't work. I must admit, I'm a noob at VPN, but I really don't have a clue, what I'm doing wrong. Perhaps you can tell me? :)

Thanks in advance!
BurtaN

PS: PPTP VPN to my university via Ubuntu works.

---

### Post by BurtaN on 2011-05-23
Ok, I've just found the solution. My password was longer than 11 chars...

Best,
BurtaN

---

