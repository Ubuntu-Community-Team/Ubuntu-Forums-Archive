---
title: "Samba Behind Router"
date: 2008-12-10
forum: Networking &amp; Wireless
---

### Post by ripken204 on 2008-12-10
i currently have a desktop and my ubuntu server on a router.
i want computers outside of my router to be able to access my samba shares on my server.

currently computers on the outside are able to view the website on apache on my server. i have done that by forwarding port 80 requests to my router to my server.

i have forwarded port 139 for samba.

right now when i am getting this in the terminal (MYIPADDRESS = an ip address):

smbclient -L //MYIPADDRESS
timeout connecting to MYIPADDRESS:445
timeout connecting to MYIPADDRESS:139
Connection to MYIPADDRESS failed (Error NT_STATUS_ACCESS_DENIED)

---

### Post by Iowan on 2008-12-11
[Here]("http://www.blisstonia.com/eolson/notes/smboverssh.php") is an article on tunneling Samba over SSH. [Another article]("http://www.linuxquestions.org/questions/linux-security-4/how-to-open-port-for-linux-samba-for-windows-users-152405/?") suggests ports 137-139 need to be forwarded (opened).

---

