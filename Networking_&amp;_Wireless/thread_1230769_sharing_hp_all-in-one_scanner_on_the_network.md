---
title: "sharing hp all-in-one scanner on the network"
date: 2009-08-03
forum: Networking &amp; Wireless
---

### Post by caue.rego on 2009-08-03
Hopefully this isn't too wrong of a place to post this repeated particularly different question.

I got an HP all-in-one and the scanner is working. The printer is working, easily shared on the network. Now I just need to share the scanner.

[https://help.ubuntu.com/community/ScanningHowTo#Server-side%20Setup%20(9.04](https://help.ubuntu.com/community/ScanningHowTo#Server-side%20Setup%20(9.04))

That doesn't work. And neither did any other info I've found so far.

list of revelant shell commands:
user@server% telnet localhost 6566 (connected to localhost - the server)
user@client% telnet ip_of_server 6566 (connected to server - from the client)
user@server% telnet localhost 6567 (connection refused - just stating the telnet is fine)
user@server% scanimage -L (returns device hp, etc)
user@server% sudo scanimage -L (samething, on the server, works fine)
user@server% xsane (brings up the gnome gui interface, all scanner working)
user@server% cat /etc/servuces |grep sane (brings sane-port 6566/tcp sane saned #SANE network scanner daemon)
user@server% sudo service saned restart (ok)
user@server% sudo -u saned scanimage -L (brings ERROR, sometimes "segmentation fault", sometimes can't find the scanner)
user@client% cat /etc/sane.d/net.conf (brings the ip_of_server)
user@client% scanimage -L (brings ERROR, can't find the scanner)

So, I guess it's a user permission thing, but I can't resolve this. I can't find the user saned, and I wouldn't know what permission to set here. Couldn't find any info on this too, and maybe I'm in the wrong path.

I also tried to *aptitude install libsane-extras*, and do everything over again, but still nothing.

Anyone can shred me some light?

Thanks.

---

### Post by caue.rego on 2009-08-04
Well, as it turns out, I could configure the permissions. Either (a step of) that or installing xinetd solved the issue. I just won't bother right now on which one.

No secret on installing xinetd: sudo aptitude install xinetd

As of setting permission, I've changed two lines on /etc/groups:
user@server% sudo gedit /etc/groups

```

lp:x:7:saned
saned:x:113:scanner

```

Problem solved.

Hopefully this may help someone else as well.

---

