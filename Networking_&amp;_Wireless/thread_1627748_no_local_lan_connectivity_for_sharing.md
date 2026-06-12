---
title: "no local lan connectivity for sharing"
date: 2010-11-21
forum: Networking &amp; Wireless
---

### Post by guest5 on 2010-11-21
I can see the network shares, but when I click on one of them, I get the message:

Unable to mount location (header)
Failed to retrieve share list from server (body)

This worked fine for me in the previous versions, so I don't know what to try.

On the windows machine, the share can also be seen but not permitted to connect.

---

### Post by guest5 on 2010-11-21
I definitely have the samba shares installed, and with the newest version, so I typed this into the terminal and got this response:

sail@sail-HP-Pavilion-dv7-Notebook-PC:~$ smbclient -L //server -U user
Enter user's password: 
Connection to server failed (Error NT_STATUS_BAD_NETWORK_NAME)

any ideas ?

---

