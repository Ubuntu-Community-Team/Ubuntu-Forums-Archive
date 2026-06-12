---
title: "FTP: 500 illegal port command: connection refused"
date: 2011-09-11
forum: Networking &amp; Wireless
---

### Post by helvecio on 2011-09-11
My NAS is behind a ActionTec MI424WR. Port 21 is open on the router. I can access FTP from the local network but not from outside (wan).
From the command line I also get FTP access from outside (wan) until I ask for 'ls' and then it comes back w/ "500 illegal port command". Server is found using its own domain, password is accepted and I can do a 'cd'.
I am using gFTP to connect and test. I have enabled PASV but keep getting either "500 illegal port command" or "connection refused". 
I have read the FTP installation tutorial in Ubuntu Forum, etc but it is hard to dig thru all that stuff and translate into specific action, test and debugging to see where the problem is.
I really appreciate the community's help.

---

### Post by SeijiSensei on 2011-09-12
Does the FTP server support PASV?  If you make a connection over the local network and use PASV, does that work?

Are you running SSH on the server?  If so, pass port 22 back to the server and try using [FISH](http://en.wikipedia.org/wiki/Files_transferred_over_shell_protocol).  I don't use GNOME, but I read recently that using Connect to Server in nautilus will use FISH to set up a file sharing connection.  We KDE folk just use fish:// URLs.

FTP is a real pain to get working through routers, especially routers where you don't have full control of the firewalling ruleset like you can with a Linux firewall using iptables.

---

### Post by helvecio on 2011-09-12
1) Thanks.
2) More info

Port 22 is being forwarded to the  NAS's internal/static IP. I can ssh to the NAS from the WAN, using its  own domain, w/o any problem.

Regarding PASV/passive, gFTP has 2 settings:
- Ignore PASV Address
- Passive File Transfers

When connecting locally (from within the LAN) I get:
----------------------------------------------------------------------
Result                      |Ignore PASV Address|Passive File Transfers
----------------------------------------------------------------------
successful connection|ON                          |OFF
successful connection|OFF                         |OFF
connection refused    |OFF                         |ON
Loading directory listing from server (LC_TIME=pt_BR.utf8)
PASV 
227 Entering Passive Mode (96,228,35,20,19,158)
Could not create a data connection: Connection refused

When trying to connect from the WAN, w/ both options OFF, I get:
Loading directory listing from server (LC_TIME=pt_BR.utf8)
PORT 192,168,1,5,197,11  (192.168.1.5 is the internal/dynamic IP of the Ubuntu/gFTP box that I test from)
500 Illegal PORT command.
Response "5" invalid from the server.

When connecting from the WAN I get:
---------------------------------------------------------------------------
Result                             |Ignore PASV Address |Passive File Transfers
---------------------------------------------------------------------------
PORT 192,168,1,5,236,108  |ON                          |OFF
500 Illegal PORT command|
---------------------------------------------------------------------
PORT 192,168,1,5,224,4    |OFF                         |OFF
500 Illegal PORT command
---------------------------------------------------------------------
connection refused           |OFF                          |ON
Loading directory listing from server (LC_TIME=pt_BR.utf8)
PASV 
227 Entering Passive Mode (96,228,35,20,19,162)
Could not create a data connection: Connection refused

When trying to connect from the LAN or WAN, w/ both options ON, gFTP closes.

gFTP issues a message just after trying to obtain a directory listing.

The server's config has:
pasv_enable=YES
pasv_promiscuous=YES
pasv_min_port=5000
pasv_max_port=5099
pasv_address=UPNP

My NAS is a Western Digital model MyBook World Edition "white lights".
There is a post related to this problem
[http://mybookworld.wikidot.com/forum/t-145232/trouble-connecting-through-ftp](http://mybookworld.wikidot.com/forum/t-145232/trouble-connecting-through-ftp)
but I don't quite follow what they are saying.

In the wiki above I understood they talk about forwarding the range  5000-5099 to the internal/static IP address of my FTP server.
In my router configuring experience I never saw the option to forward a range of ports, usually only 1 port at a time.

---

### Post by SeijiSensei on 2011-09-12
First, I didn't know that the NAS was working as the FTP server.  I thought you had it connected as a drive to an Ubuntu server and was looking for help with the latter.

Second, perhaps you don't need to open up that entire range of ports if you're only supporting a single user.  Try forwarding one or two ports in the 5000+ range and change the settings on the NAS accordingly.

Beyond that I can't help much.  Maybe there's someone here who has the identical hardware you do.

---

### Post by helvecio on 2011-09-12
Got it to work.
The FTP server requires ports 5000-5099 to be forwarded to the server (that I knew).
What I did not know is that the interface of the Actiontec requires that the source be 'any' and the destination "5000-5099". Do **not** set source to "5000-5099".
Thanks Seiji for making me even more stubborn.

---

