---
title: "Quick Samba Question"
date: 2009-06-16
forum: Networking &amp; Wireless
---

### Post by blsbball on 2009-06-16
So after a couple days of pain I finally got Samba desktop to play nice with my vista laptop. I am now concentrating on trying to secure things. I was wondering how can I make it so I have to login with a password and username when I access the shares from ubuntu-desktop via vista?
Thanks

---

### Post by updog on 2009-06-16
First off, let me say I'm relatively new to Ubuntu server as well so I apologize if I am unclear or misinformative.  But in setting up my office LAN with a Ubuntu 9.04 (upgraded from 8.01) and a variety of client platforms (mostly 32-bit Vista machines), all I had to do was: 

Creat a user account on the server with the "Users and Groups" menu option from the System->Administration-> drop down menu

Then using Webmin 1.420, go to "Servers" -> Samba Windows File Sharing" -> "Convert Unix Users to Samba Users".

Then go to your client (vista) machine and go to "my computer" and "map network drive"

Assign a drive letter (Z: by default) and map the drive to the host location:

     eg.  \\servername  or \\servername\publicsharename

and connect.  That should prompt you for the username and password.  There is also a 'connect using a different user name" option on the network drive mapping window if you ever want to switch users (helpful if you utilize the samba\home directories).

hope this helps.

---

### Post by Iowan on 2009-06-16
Depends a lot on how you set things up - did you configure shares from /etc/samba/smb.conf or did you set up shares from Nautilus? [Here]("https://help.ubuntu.com/8.10/internet/C/networking-shares.html") is a help page.  If you set it up the right way ( ;) ) via smb.conf, what did you use for **security= ** setting?

---

### Post by blsbball on 2009-06-16
i went into the config file and just changed the browseable to yes and didnt mess with the security...should i go back in? if so what do I change?

---

### Post by Iowan on 2009-06-16
**security = user** is suggested (recommended?) in smb.conf - but is commented out. Uncommenting it (delete the leading semicolon) will require each user to have a valid Linux and Samba account (check **man smbpasswd**).

---

### Post by blsbball on 2009-06-17
Ok so I uncommented the user but now the ubuntu desktop doesnt show up in the "network" on vista. Is there something else Im supposed to do? thanks

---

