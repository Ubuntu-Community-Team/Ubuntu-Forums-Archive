---
title: "Samba fights WebDAV, WebDAV wins, Windows looses."
date: 2009-05-20
forum: Networking &amp; Wireless
---

### Post by iva2k on 2009-05-20
Hi Gang. I just found an answer to a nasty Samba problem that I was having since upgrading my server to Intrepid 8.10

First the problem:

Every single Windows machine (all Win XP) on my home network once in a while looses connection (mapping) of network drives from Samba. It keeps seeing other Windows machine shares, but not Ubuntu. It started happening right after upgrade to Intrepid 8.10.

If I try to open shared location by UNC, such as \\fs\share1, I'm getting a request for the password, but nothing happens after password entry - the password dialog keeps coming back. If I enter \\fs in Explorer, it opens an empty view under My Network Places > Entire Network > Web Client Network, not under Microsoft Windows Network as it would happen normally when Samba connection works. Needless to say that all the shares from that server fall off at that time, and cannot be reconnected by any woodoo that I could think of with that machine (reboots, moving the order of providers for Web Client Network, etc.)

Peculiar part is that all other machines were quite happy and can see the shares.

My server is configured to run Samba+winbind, Apache and has WebDAV module for apache. It is further configured as wins server for the network.

I found one temporary rework - if I stop apache server, restart samba and restart windows machine that flaked out, then I can reconnect the shares. Then I can restart apache, and all seems normal again, until this or some other machine flakes out.

I searched the net low and high for many days. Noone seems to encounter that exact problem like I did, but some pointers suggested that WebDAV handling on Windows has problems.

I'll get to the final solution in a follow-up comment...

---

### Post by iva2k on 2009-05-21
Now I continue to my analysis (read next note for the final solution):

It appears that Intrepid 8.10 introduced daemons vs. inet RUN_MODE in /etc/default/samba, and it prefers to switch it to "inet". 

What it means in practice, is that inet (being from xinetd or inetd package) is responsible to start samba as soon as any client machine tries to open its socket.

My guess is that this additional time that is required to start new process, load it from disk, let it read its config files, and finally respond to the request, it causes windows smb/cifs to timeout (it is my pure speculation), and this causes windows to go further down the list of providers to WebDAV service, which finds apache/WebDAV on the same server, happily reports that there is in fact such resource, and it kicks SMB share into this WebDAV mode which does not have a simple recovery.

---

### Post by iva2k on 2009-05-21
Here's the solution:

On the Ubuntu server issue this command in terminal:
```
sudo nano /etc/default/samba
```

Change RUN_MODE=inet to RUN_MODE=daemons, save, restart the server, and see that Windows now finds the shares all the time.

---

