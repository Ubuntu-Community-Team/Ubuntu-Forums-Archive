---
title: "Selective Networking"
date: 2011-08-08
forum: Networking &amp; Wireless
---

### Post by KingHippo on 2011-08-08
Let me preface this thread by saying I am not a network expert and have a marginal understanding of TCP/IP.  So please go easy on this newb.

also 
> Sorry - no matches. Please try some different terms.  

[SIZE=3]The Question:[/SIZE] 
How can I route traffic destined for a certain network say 10.10.x.x to adapter X say... Eth08 and traffic destined to anywhere else to eth0?


[SIZE=3]The Back Story:[/SIZE]
I am using the latest ubuntu and am connecting to a work VPN through a VPNC connection.  I also connect through my dsl modem to the internet for browsing.

I did a bit of wiresharking and it would appear that all HTTP packets are sent thru the VPN tunnel connection and then the vpn decides whether it's on their network or not and if not, rejects it. 

At this point the packet is sent through my dsl modem and off it goes to the internet to bring magic to my computer.

Assuming my basic reasoning of how this works is correct, every http request I send on my computer is going through the work vpn.  

For personal reasons, I would rather not be sending youtube.com or other "non work related" requests through my VPN for the company to log and get angry.

[SIZE=3]Lame Attempt At Workaround:
[/SIZE]To prove that I'm not completely useless here guys... I thought of one crappy workaround.  I guess I could use a SSH tunnel and a SOCKS proxy along with Firefox plugin FoxyProxy to decide what traffic goes thru my tunnel or through the default adapter.  This solution just stinks to me and I am sure there is an easier way to go about doing this.

---

