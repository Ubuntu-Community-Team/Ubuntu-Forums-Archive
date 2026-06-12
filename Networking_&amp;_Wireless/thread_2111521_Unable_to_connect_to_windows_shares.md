---
title: "Unable to connect to windows shares"
date: 2013-02-02
forum: Networking &amp; Wireless
---

### Post by musshan on 2013-02-02
Hello Mates,

I am using Lubuntu 12.10. When I try to connect using GUI (File  Manager-Network Connections), it doesn't connect and says timeout.


In Terminal I am getting the following

  john@Laptop:~$ smbtree Enter john's password:  MYHOME     \\LAPTOP                Laptop server (Samba, Ubuntu)         \\LAPTOP\print$         Printer Drivers         \\LAPTOP\John           Lubuntu-Laptop-Home         \\LAPTOP\IPC$           IPC Service (Laptop server (Samba, Ubuntu))     \\DESKTOP                john@Laptop:~$ smbclient -L Desktop -U John Enter Jim's password:  Connection to Desktop failed (Error NT_STATUS_UNSUCCESSFUL)   But when I substitute smbclient -L Desktop -U John with smbclient -L ip.address. -U John instantly it shows all the shares.

Please help me solve this guys. Thanks

---

