---
title: "Shorewall / DDOS-Deflate Configuration"
date: 2012-07-17
forum: Networking &amp; Wireless
---

### Post by svtguy88 on 2012-07-17
A friend of mine recently took me down using a DDOS.  I know there isn't really a fool-proof way to safeguard against this, but it got me thinking about beefing up my security a bit.

From what my logs show, the 'attack' came from 4 IPs for about three minutes.  

I did some research, and a script/program called "DDOS-Deflate" is about the best I can find for this sort of thing.  It basically checks how many connections a given IP has, and if it's over a certain amount in a period of time, the IP gets blacklisted via iptables.

This all seems like it should work fine, but I ran some tests, and it's not catching things the way I'd like it to.

My system configuration is as follows:

-Ubuntu 12.04 running Shorewall, acting as firewall and router via 4-port ethernet card
--Apache server in Debian LXC container
--Postgre server in Debian LXC container
--Email server (Postfix/Dovecot) in Debian LXC container

Each of the containers runs through a common network bridge (br0) which Shorewall then turns into a subnet that holds just my containers.  Each port of the 4-port NIC also runs it's own subnet.

The problem is that when I try to run a DOS attack against my Apache server, the DDOS-Deflate script doesn't seem to see the connections being created.  I haven't tested it from the outside yet, but I'd expect similar results.

I looked around a bit on Google, and had a peek at /usr/local/ddos.conf and /usr/local/ddos.sh

For those unfamiliar with DDOS-Deflate, it can be found [here]("http://deflate.medialayer.com/").  The line in the script that actually checks the connections looks like this (actually, this is a patched one I found online, as the one that comes with the script has a problem - [info here toward the bottom]("https://mangesh7rhcss.wordpress.com/2011/03/02/dos-deflate-installation/")).

```
netstat -ntu | grep ':' | awk '{print $5}' | sed 's/::ffff://' | cut -f1 -d ':' | sort | uniq -c | sort -nr > $BAD_IP_LIST

```

So, I ended up running a DOS attack a few times from my development box to the server, and testing how many connections this script was seeing by manually running netstat on the server via SSH.  To my dismay, the only connections that it saw from my dev box to the server were the 3 SSH connections I had open.  Apparently, my Shorewall rules are forwarding the requests immediately to the web server container before DDOS-deflate has a chance to analyze the traffic?

Any other ideas?  I'm kinda shooting in the dark here.  That's all I can think of though, as even if I simply open a web page (dev box to server's web server container), and then run netstat on the host OS of the server, it still doesn't see my HTTP connection.  

My only idea is to move DDOS-deflate to inside the containers, and see if it catches rogue traffic there, after it's been forwarded to the container by Shorewall.  I was hoping having it installed on the host OS would have worked...

Sorry for the lengthy post...let me know if I can clear anything up.

---

### Post by svtguy88 on 2012-07-19
I don't remember this forum's bumping guidelines, but....bump.

I sent an email to the shorewall-users mailing list...hopefully they will have some ideas.

---

