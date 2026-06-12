---
title: "file sharing ubuntu xp"
date: 2006-01-28
forum: Networking &amp; Wireless
---

### Post by cmongini on 2006-01-28
hi, 
i have the following configuration.
linux with eth0 (internet) and eth1 ( local network to laptop with win xp.
the laptop gets online thru the linux pc but i can´t find a possibility to share the files on the two computers.  when i ftp the laptop from the linux i don´t get any response. i downloaded already samba but there is no graphical interface?? ( i can´t open the application) is there a simple GUI application that would do the job? 
thanks

---

### Post by amohanty on 2006-01-28
1. Enabled file and printer sharing on the _laptop_
2. Places->Network Servers->provide workgroup, username and password (if the shared dir on the laptop is not open to all) and connect.

> when i ftp the laptop from the linux i don´t get any response.
For this you will need an FTP server running on the laptop.

HTH
AM

---

### Post by cmongini on 2006-01-28
thanks, just a prob: i found the network icon, following your description, but if i double click, it is empty! 
(on the laptop i enabled for everybody a whole drive!) any hints?

---

### Post by amohanty on 2006-01-29
Ok then check:
1. Is your samba daemon running.
2. That a valid user has been added using smbadduser
3. You are using the valid username or password

Alternatively:
Places->Connect to server->Windows share then provide the _exact_ share name, windows username, password and workgroup.

HTH
AM

---

### Post by cmongini on 2006-01-29
although i spent already some time configuring samba it´s not working ( probably because of download probs) 
anyway your second suggestion works! thanks

---

