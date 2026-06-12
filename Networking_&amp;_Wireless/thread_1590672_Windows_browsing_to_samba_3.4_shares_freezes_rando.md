---
title: "Windows browsing to samba 3.4 shares freezes randomly"
date: 2010-10-08
forum: Networking &amp; Wireless
---

### Post by betty85 on 2010-10-08
Hi All

First time posting, please bear with me!

I have an Ubuntu Server 9.10 box running Samba 3.4.0. It has  4 shares, one of which is a CIFS connection to an XP machine, another of which is a password protected share.

All the shares work fine and well. However, lately the client has called to say that "everything's hanging and freezing" when they browse the shares via Windows Explorer (approximately 30+ PCs on network, variety of XP, Vista and 7 OSes). Not all users always experience the problem, and I remote in to test when I hear this via an XP machine, and today for the fist time I also experienced this problem - browsing literally sticks and hangs. No entries in PC's eventviewer. 

They are running on Netgear switches, all the same age, a couple of months old.

I've browsed through numerous forums and haven't found anything that answers my question - what's going on! A simple reboot and and everything's fine again for an indeterminable time, then I get another phonecall and an unhappy client on the end!:confused:

---

### Post by luvshines on 2010-10-08
Though I am not sure but you may want to check the logs on Samba server side when this happens. See if you can get something useful out of there.

Also, when one machine hangs, whether server permits more connections or not.

---

### Post by betty85 on 2010-10-08
Hi luvshines, thanks for your reply.

I'm not sure which log file exactly to check? The smbd.log file has entries from quite a few days ago, none on the days that this freezing has occurred - is there another one I should be checking? 

The server does allow more connections as when the client contacts me, I can remote in and test too (and subsequently hang as well)

---

### Post by luvshines on 2010-10-08
Since the log file has %m , each connecting IP should have its own log file, log.__ffff__<IP>. That is how I have it in /var/log/samba

You may also increase the 'log level' maybe 5 or 6, in smb.conf which defaults to 0 [ Set log level = 6 in smb.conf and reload smb service ]

---

### Post by betty85 on 2010-10-08
Yes I've understood that that's what the log file template signifies - would that suggest that there may be multiple similar entries in each client's log?

What does increasing the log level do?

---

### Post by dtfinch on 2010-10-08
Years ago I used to see freezes caused by the WebClient service trying to connect and timing out before falling back to using SMB/CIFS. With most servers, it'd fail quickly and the behavior would go unnoticed, but sometimes port 80 would be firewalled, causing a timeout, or maybe (I can't remember) WebClient would fail to get the right IP from DNS, but when connecting to the CIFS share it would get the correct IP from WINS.

[http://support.microsoft.com/kb/832161](http://support.microsoft.com/kb/832161)

Though the article suggests that the problem may have been fixed in XP SP1, and I personally don't recall running into this problem recently. If it is a issue with WebClient, simply disabling the service (which also breaks WebDav which few people ever use) should make the delays go away.

Speaking of DNS, you should probably make sure that they have a DNS server, that computers on the network are actually using it, and that the Samba server resolves correctly. If it's not, the delay might be the DNS request timing out, then falling back to WINS or something else.

---

### Post by betty85 on 2010-10-20
Hi dtfinch, thanks for you reply. What I don't understand though is if it is a client (Windows) problem, then why would rebooting the server fix the problem? As soon as I reboot it and it comes up again all is happy. The one thing though, the server mounts a share on another XP box at boot (which it regularly fails to do) and then shares it also via Samba - could this have any influence?

This happened again yesterday and I tried rebooting the Samba daemon and that didn't help - a full reboot of the server did though, as always.

---

### Post by betty85 on 2010-10-20
Would the maximum number of files open have anything to do with it?

---

### Post by betty85 on 2010-11-24
or perhaps entries in the samba logs per pc like the following:

 <share_name> has wide links and unix extensions enabled. These parameters are incompatible. Wide links will be disabled for this share.

?

---

### Post by betty85 on 2010-11-26
*bump*

---

### Post by stallinux on 2011-11-05
Same problem here. Samba freezes up randomly on average after about 1 minute of file transfer. (Anything between 5 seconds and 20 minutes).

Tried many things and combinations:
Wireless connection from (any) Ubuntu to (any) router and (any) NAS (Network Attached Storage, running also Linux).

Then I found out that when keeping in parallel interactivity going with the system it would not hang. So, while transferring a large file, in another window I would keep browsing (reload, reload, reload, etc.). No hang. We even wrote a small script to keep asking for directory contents every 10 seconds. Not very elegant, but it worked.

W****s on the same machine, connected the same way to the same NAS gave no problems. It is an Ubuntu problem! (Did not try other versions of Linux).

Now I switched to 11.10/64, and while they obviously spent a lot of effort in placing all the things (such as buttons) in the wrong places, the irritating bugs remain. It still annoyingly hangs. Instead of that stupid Unity, I wish they would spend time on Integrity :-)

---

