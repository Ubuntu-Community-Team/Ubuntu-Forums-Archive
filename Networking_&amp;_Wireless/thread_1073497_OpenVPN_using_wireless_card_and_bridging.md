---
title: "OpenVPN using wireless card and bridging?"
date: 2009-02-18
forum: Networking &amp; Wireless
---

### Post by momitty on 2009-02-18
Please let me know if this is possible:

I have a Ubuntu 8.10 computer that I want to make a VPN server.  I want to set it in my garage cause it's old and the fan is loud and sometimes I want to browse the internet in my garage... so it has a wireless PCI card in it (the garage is detached and there isn't a good way to run a cable out there and I've used the wireless card in here for awhile and it works fine, other than the keyring box that keeps popping up)

What I'd like to do is forward the necessary ports on my DSL router to the VPN box.

#1  Is this possible using a wireless card?  It doesn't seem to show up as eth0 and I don't see it in the interfaces file and all of the documentation I have found uses eth0.

#2  Can I do it this way?  The bridging method makes it appear you can, but I'm not finding great documentation on it.  I'm not experienced enough in this to just forge ahead without some documentation or help from a forum :)

Thanks!

---

### Post by superprash2003 on 2009-02-18
1)it neednt be eth0
2)[http://ubuntuforums.org/showthread.php?t=1064776](http://ubuntuforums.org/showthread.php?t=1064776)

---

### Post by momitty on 2009-02-18
On these lines...

localip 192.168.0.1
remoteip 192.168.1.1-255

My router happens to be 192.168.0.1 so does that really mean my router, or the server?

Can the remote IP's be on the same subnet?  All my computers are 192.168.0.xxx or do they have to be on a different subnet like .1.xxx instead of .0.xxx?

Does this solution let Windows clients into the server too?

Thanks for the help!

---

### Post by momitty on 2009-02-18
Also, on these lines...

[SIZE="1"]# nat Table rules
*nat
:POSTROUTING ACCEPT [0:0]

# Forward traffic from eth1 through eth0.
-A POSTROUTING -s 192.168.0.0/24 -o eth0 -j MASQUERADE

# don't delete the 'COMMIT' line or these nat table rules won't be processed
COMMIT[/SIZE]

I had intended on using the bridging/tap/stuff in openvpn which appears that it only requires one ethernet card (in this case wireless card).  And since I don't have eth0 (it looks like maybe it's ath0 ?)  do I sub ath0 for anywhere there is eth0?

---

