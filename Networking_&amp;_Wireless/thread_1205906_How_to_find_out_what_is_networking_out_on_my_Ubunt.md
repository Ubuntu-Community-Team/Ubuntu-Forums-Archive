---
title: "How to find out what is networking out on my Ubuntu ?"
date: 2009-07-06
forum: Networking &amp; Wireless
---

### Post by Browser_ice on 2009-07-06
I have noticed that lately my network connection is always sending out (1k/s).  I have checked in the system monitor and see nothing active enough to tell me what it is.

How can I find out what is constantly networking out of my Ubuntu 8.10 ?

I found that out through a VPN connection I sometimes use at the office. Before, it usually showed very little network ativities. But lately, it is showing a constant activity of sending out to somewhere. If I close my VPN and go into the system monitor, the networking out is still going on without interruptions.

20 min after booting time, it sent out 1M and received 200k. My connection was not that active before even if I am doing nothing at all on my Ubuntu.

---

### Post by mhgsys on 2009-07-06
You could use iptraf to monitor your network traffic;

```

sudo apt-get install iptraf

```

after that just run iptraf as root in terminal or console
```

sudo iptraf

```

---

### Post by Browser_ice on 2009-07-06
Thx, I'll check it out.

What about ntop ?  I saw mentions of it but when I installed it, running in a terminal does not show me any usefull infos.

---

### Post by jonobr on 2009-07-06
hello


May also be worth your while turning off anything requiring network connections
browser
IM/pidgin
twitter
etc....

Then run a 

```
sudo tcpdump -w trace.pcap -s 0 -i any 
```

You could open the resulting file in wireshark

That will show you any packets your sending.
Sometimes though it makes you go down rabbit holes that look bad but arent really.

---

### Post by mhgsys on 2009-07-06
IPTRAF : iptraf is an ncurses-based IP LAN monitor that generates
various network statistics including TCP info, UDP counts, ICMP and OSPF
information, Ethernet load info, node stats, IP checksum errors, and others

NTOP : ntop shows the current network usage. It displays a list of hosts
that are currently using the network and reports information concerning
the (IP and non-IP) traffic generated and received by each host. ntop
may operate as a front-end collector (sFlow and/or netFlow plugins) or
as a stand-alone collector/display program. A web browser is needed to
access the information captured by the ntop program.

---

### Post by Browser_ice on 2009-07-06
Well so far, with iptraf, I am seeing a constant traffic about UDP sending from bootps ip to a bootpc ip. Its about every seconds.

What is that thing ?

Did a bit of search on bootpc and bootps. It seams to be related a DHCP server where my PC is requesting somekind of IP assigned lookup. But why does it need to do it every seconds ?  Aren't assigned IP from DHCP servers good for weeks/months ?

I am also assuming that (see P.S. note) I did not used to see this because it was stopped at my router.

p.s.: I forgot to mention something, I used to have a router (for years) between my PC and my modem cable. It died last month and my modem cable had to be replaced.

---

### Post by mhgsys on 2009-07-06
I'm really not an expert in monitoring ip traffic, though if it's UDP sending from bootps ip to a bootpc ip (I assumed this is your boot pc correct>? lol)

I assume it's ok, and it's probably samba or nfs looking for shares / other pc's in the network.

The only way I know to block it (when really wanted) is with firestarter /firewall

Then again; I'm really not an expert in monitoring ip traffic

So maybe someone else could provide you with more information if needed.

---

