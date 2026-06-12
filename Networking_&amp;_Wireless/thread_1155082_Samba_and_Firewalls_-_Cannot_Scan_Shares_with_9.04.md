---
title: "Samba and Firewalls - Cannot Scan Shares with 9.04"
date: 2009-05-10
forum: Networking &amp; Wireless
---

### Post by ve4cib on 2009-05-10
This is a really weird error that's been bothering me for a couple of weeks:

When I have my firewall enabled I am incapable of scanning Samba shares.  smbtree returns no output, Nautilus says that it could not retrieve the share list from the server, and PyNeighborhood simply fails to return any results.

I have three computers at home: a Windows XP desktop ("Marvin"), a laptop running 8.04 ("Ubik") and a laptop running 9.04 ("Tosh").  Tosh got a clean install of 9.04 the first weekend it was available, and has been updated fully since then.

Ubik and Marvin can both scan all of the shared folders on the network just fine:

```
ve4cib@Ubik:~$ smbtree
Password: 
IBIS
	\\UBIK           		Ubik server (Samba, Ubuntu)
		\\UBIK\LaserJet       	HP LaserJet 1020
		\\UBIK\PDF            	PDF
		\\UBIK\print$         	Printer Drivers
		\\UBIK\music          	Enjoy some of my tunes
		\\UBIK\video          	Why not watch a movie?
		\\UBIK\radio          	Enjoy some radio plays and streaming audio
		\\UBIK\IPC$           	IPC Service (Ubik server (Samba, Ubuntu))
	\\TOSH           		Tosh server (Samba, Ubuntu)
		\\TOSH\LaserJet       	HP LaserJet 1020
		\\TOSH\PDF            	PDF
		\\TOSH\print$         	Printer Drivers
		\\TOSH\music          	Enjoy some tunes
		\\TOSH\video          	Sit back and watch a movie
		\\TOSH\IPC$           	IPC Service (Tosh server (Samba, Ubuntu))
	\\MARVIN         		Marvin
		\\MARVIN\BubbleJet      	Canon S900 (Copy 1)
		\\MARVIN\LaserJet       	HP LaserJet 1020
		\\MARVIN\print$         	Printer Drivers
		\\MARVIN\SharedDocs     	
		\\MARVIN\IPC$           	Remote IPC

```

The problem is with Tosh.  When I enable the firewall this is what I get:

```
ve4cib@Tosh:~$ smbtree
Password:

```

Interestingly when I use Nautilus and navigate to smb://Ubik I get a listing of all of the shares on that device.  So clearly the problem isn't with Samba scanning individual hosts, but rather the problem lies with trying to scan the entire network.

When I disable the firewall and everything works fine on Tosh.  **But I am using the exact same IPTables rules on all three machines**.  Obviously the problem has something to do with my firewall configuration, but I have absolutely no idea what that is.

I've configured the firewall using GUFW.  Here are the rules I am using on all three machines:

```

### TUPLE ### ALLOW ANY 21 0.0.0.0/0 ANY 192.168.1.0/24
### TUPLE ### ALLOW ANY 22 0.0.0.0/0 ANY 192.168.1.0/24
### TUPLE ### ALLOW ANY 137 0.0.0.0/0 ANY 192.168.1.0/24
### TUPLE ### ALLOW ANY 138 0.0.0.0/0 ANY 192.168.1.0/24
### TUPLE ### ALLOW ANY 139 0.0.0.0/0 ANY 192.168.1.0/24
### TUPLE ### ALLOW ANY 445 0.0.0.0/0 ANY 192.168.1.0/24

```

I've looked at the system logs to see if the firewall is logging anything, but there is no evidence of dropped packets in the logs.  (UFW logging is turned on.)

Frankly I am at a loss at this point.  Does Samba in 9.04 require additional ports?  Or has GUFW somehow decided to block outgoing traffic on certain ports and not log it?  ...?

Any advice or suggestions the community can offer would be greatly appreciated.  Thanks a lot!

---

### Post by Lety on 2009-06-19
This may help:
```
sudo ufw allow Samba
```
Helped with me with Gufw 9.04.2 in Jaunty (a new rule for Samba appeared automatically in Gufw).

---

