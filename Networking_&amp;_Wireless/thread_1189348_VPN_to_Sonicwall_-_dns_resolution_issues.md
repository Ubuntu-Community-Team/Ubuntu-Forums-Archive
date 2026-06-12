---
title: "VPN to Sonicwall - dns resolution issues"
date: 2009-06-16
forum: Networking &amp; Wireless
---

### Post by mr_Frank on 2009-06-16
Hi everybody, 

I'm trying to create  a VPN connection from home to office......

at home side: HP desktop pc with Ubuntu linux 9.04
at office side Sonicwall TZ-170 Firewall....

I've found and followed this forum topic:
[http://ubuntuforums.org/showthread.php?t=527423](http://ubuntuforums.org/showthread.php?t=527423)

with some ours of testing I've actully able to complete a manual connection.....
packets are traveling into the VPN tunnel (i can ping any office IP from my home workstation)

I've found another fine document that helped me in understanding and reach a stable configuration....
it was a text file written by an italian teacher (I think) to explain how to setup a vpn connection to his school network!!!
nere is the link:
[http://cafim.sssup.it/~giulio/other/howto_vpn_sssup.txt]("http://cafim.sssup.it/%7Egiulio/other/howto_vpn_sssup.txt")

into this document I've found a lot of informations and a very interesting link to a scrip used to activate the VPN connection in "automatic" mode (without user interaction), the link is near the end of the textfile I've mentioned some rows ago......

merging this informations helped me a lot.......

so I've thinked to post these references joined to help other people......

actually the VPN conneciton is working....
but i'm not able to correctly setup dnsmasq.....

I've modified the dnsmasq.conf file to reflect my office domain information adding lines for dns forwarding to the office dns servers......


*server=/myoffice.local/xxx.yyy.[www.zzz]("http://www.zzz")*

[FONT=Verdana]
local resolver configuration in /etc/resolv.conf file points to localhost only....
if I stop dnsmasq service i'm not able to browse the web.....
so i can think dnsmasq is workign properly......

if i use nslookup tool....

any fqdn query to the office domain made against localhost server is returning a valid 
and real ip address ie.: server01.myoffice.local

root@myworkstaion:/etc/vpnc# nslookup 
> server
Default server: 127.0.0.1
Address: 127.0.0.1#53
server01.myoffice.local
xxx.yyy.[www.nnn]("http://www.nnn")

but ping seem to be unable to correctly resolve hostname to ip...

[/FONT][FONT=Verdana]root@myworkstaion[/FONT][FONT=Verdana]:/etc/vpnc# ping server01.nyoffice.local
ping: unknown host server01.nyoffice.local

[/FONT][FONT=Verdana]is there someone who can tell me where is the trouble??

waiting your answers......

thanks agaiin for your time, 

by francesco

[/FONT][FONT=Verdana]

[/FONT][FONT=Verdana]

[/FONT]

---

