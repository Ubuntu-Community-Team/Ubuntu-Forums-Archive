---
title: "Confusing port forwarding"
date: 2010-10-03
forum: Networking &amp; Wireless
---

### Post by ubun2ibun3 on 2010-10-03
Ok, so I'm trying to enable port forwarding so I can use my computer as an FTP server to some friends.  Here's my setup:

CLEAR wireless modem <--> LAN port 4 on router (not WAN) 
and
LAN port 1 on router <---> eth0 in Ubuntu 9.10

The modem acts as a DHCP server which successfully assigns an IP address to my desktop system.  I can also go onto the internet just fine on my desktop, and any other computer that connects to the router.

I have enabled port forwarding on the modem (not the router because it's being used as a switch, and not using its WAN port) to forward ports 21 and 80 to my desktop.  What I don't understand, though, is that when I try to FTP to the modem's WAN IP address, the connection is refused.  However, when I use websites such as:

[www.canyouseeme.org]("http://www.canyouseeme.org")
[www.yougetsignal.com/tools/]("http://www.yougetsignal.com/tools/")**open**-**ports**/

They say ports 21 and 80 are open (and not other random ports like 22 or 23 which I tried to see if the site simply said everything was open) but I cannot access my site from a web browser.

I was wondering what it was that's stopping computers from the Internet from communicating with my computer?  The modem?  The router?  Configs?

Any help would be extremely appreciated!

---

### Post by joberly on 2010-10-03
If you are trying to do this from inside the network, it will give you problems. Basically, you're router "knows" your external IP and will not actually route your request out to the internet, and back to you.

Have you tried seeing if your friend can connect from his computer outside of your network?

---

### Post by oregonbob on 2010-10-03
A classic ftp problem with port forwarding is that it needs to be ftp passive mode. Check that too.

---

### Post by ubun2ibun3 on 2010-10-04
Oh wow! Thanks, you're right!  It won't work for me to use my WAN IP, but it works for my friends!  Thanks a bunch!

---

