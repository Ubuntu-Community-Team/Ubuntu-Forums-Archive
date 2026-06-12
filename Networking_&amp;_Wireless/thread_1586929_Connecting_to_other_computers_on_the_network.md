---
title: "Connecting to other computers on the network"
date: 2010-10-02
forum: Networking &amp; Wireless
---

### Post by slowjim on 2010-10-02
When I try to use Nautilus to connect to another computer on my network, and I attempt to connect using the name of the Windows XP computer I am connecting to, I get the following error;

Could not display "smb://computername/".
Error: Failed to retrieve share list from server
Please select another viewer and try again.

However when I attempt to connect using the IP address on the network, it connects instantly.

smb://192.168.1.101/

Why doesn't it connect using the computer's name? What am I doing wrong?

---

### Post by spiky001 on 2010-10-02
You have to associate ip add with a name in network hosts if you google you will find it

Try /etc/host     I think you add ipaddress    then  pc name    follow whats in there

---

### Post by whitehaint on 2010-10-02
Same issue here, it'll go using the ip but trying to use network it stalls.  Connecting smb://workgroup/


Would the hosts file need to have the ip of the destination or origin computer?

---

### Post by spiky001 on 2010-10-03
Ok I have just checked mine I connect over Lan, i connect to machine 10.42.43.1 which is the internal ip, the name of the pc I connect to is **fred** so I edit file on the machine i,m using to connect laptop /etc/hosts I add a line 
```
127.0.0.1    linux    localhost.localdomain    localhost
127.0.1.1    linux
**10.42.43.1      fred**
```restart network should all work  username@fred

---

