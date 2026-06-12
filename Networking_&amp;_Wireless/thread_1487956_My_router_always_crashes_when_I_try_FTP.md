---
title: "My router always crashes when I try FTP"
date: 2010-05-19
forum: Networking &amp; Wireless
---

### Post by robofighter on 2010-05-19
When ever I try to do an FTP command from a remote network (works fine from a local network), my Motorola SMB1000 router ALWAYS reboot when I attempt this.

This really makes it difficult to directly transfer files to my home server from my remote location (namely homework I did at my college).

---

### Post by puppywhacker on 2010-05-19
try updating the firmware of the box, or use different methods of file transfer like SFTP. The thing with FTP is that it opens a control tcp-session to port 21 and a tcp-session to port 20 for data, and probably the last stage makes the Motorola "uncomfortable". In contrast SFTP uses a single SSH connection which simplifies the amount of work the router has to do. Using FTP transmits passwords in cleartext while SSH doesn't.

you can use the "ssh-server" to enable the SFTP server, if your router should port-forward use tcp port 22.

In windows winscp is a nice program, while in linux you can use nautilus the file explorer.

---

### Post by robofighter on 2010-05-19
Firmware is not user upgradable. SSH works ok.

Anyway is Filezilla compatible with FTPS or SFTP?

---

### Post by puppywhacker on 2010-05-20
Filezilla support SFTP. and perhaps FTPS 

The difference is that SFTP runs as file-server application of SSH and FTPS runs FTP in an TLS tunnel.

---

