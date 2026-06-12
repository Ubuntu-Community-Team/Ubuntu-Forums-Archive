---
title: "setting up a proxy server"
date: 2006-03-02
forum: Networking &amp; Wireless
---

### Post by donnysrx on 2006-03-02
hi

I got a windoze Pc using winproxy to run my home network( with FTP and Web servers on it too),all running fine ,just the trial period is about to run-out on winproxy.

I used to use ip-cop for my routing needs,but I had to have  2 PC's running all time to use bittorrents ;) . unnecessary power usage I think.

So my plan is to replace the one windows PC (with its ftp,web servers and its bittorrent downloads for my missed TV shows), with a ubuntu PC ,which I am using now, through winproxy still on the windoze PC.

winproxy provides:

A Firewall

HTTP
FTP
Telnet
Mail
News
SOCKS 4&5 
DNS
DHCP
AOL
Transparent proxy

So I need to reproduce all of this on my ubuntu box.

I've got squid 3.0 ready to install,i can follow the instructions for that I think.(From what I've read squid has got an transparent proxy which seems to be necessary for MSN(all though sometimes I've got it to connect through Socks,I got 4 PC's in the house,everyone uses MSN,In fact my wife gets me to top her wine up using it. also "steam" is a bit fussy about proxies)

I'm not sure about firewalls,I've read about using linux iptables(Is this NAT type firewalling). or do I use a firwall package,"firestarter" seems to jump to mind,must have read about it somwhere

ClamAV will this monitor the squid proxy HTTP traffic for windows type viruses.

DHCP client is in synaptic packages so I think thats not a problem.

Socks 4&5 I dont know what to do with?

Any help with packages or software I could use would be great

TIA

---

### Post by donnysrx on 2006-03-13
hi all


i got it going using firestarter and dnsmasq just got to find out if clamav can monitor the http traffic,cheers

---

