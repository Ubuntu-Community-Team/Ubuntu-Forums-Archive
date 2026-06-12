---
title: "SAMBA: ip works, name not"
date: 2011-01-24
forum: Networking &amp; Wireless
---

### Post by wschulte on 2011-01-24
I am trying to setup a Ubuntu 10.04 machine for SAMBA. Somehow imake a mistake, but what.
What works:
[FONT=Courier New][SIZE=3]  smbclient -L 127.0.0.1
  smbclient -L 192.168.1.46   # a windows XP machine named homeserver
  ping ubuntu
  ping homeserver[/SIZE][/FONT]
What doesnt work:
[FONT=Courier New]  smbclient -L 192.168.1.56    # Ubuntus address on eth0
  --> Connection to 192.168.1.56 failed (Error NT_STATUS_CONNECTION_REFUSED)
  smbclient -L ubuntu              # ubuntus name
  --> Connection to ubuntu failed (Error NT_STATUS_NETWORK_UNREACHABLE)
  smbclient -L homeserver
  --> [/FONT]Connection to homeserver failed (Error NT_STATUS_BAD_NETWORK_NAME)
Here is what netstat -anp shows for samba ports:
[FONT=Courier New][SIZE=2]  root@Ubuntu:~# netstat -anp | grep mbd
  tcp        0      0 192.168.1.0:445         0.0.0.0:*               LISTEN      1856/smbd       
  tcp        0      0 127.0.0.1:445           0.0.0.0:*               LISTEN      1856/smbd       
  tcp        0      0 192.168.1.0:139         0.0.0.0:*               LISTEN      1856/smbd       
  tcp        0      0 127.0.0.1:139           0.0.0.0:*               LISTEN      1856/smbd       
  udp        0      0 192.168.1.0:137         0.0.0.0:*                           1850/nmbd       
  udp        0      0 0.0.0.0:137             0.0.0.0:*                           1850/nmbd       
  udp        0      0 192.168.1.0:138         0.0.0.0:*                           1850/nmbd       
  udp        0      0 0.0.0.0:138             0.0.0.0:*                           1850/nmbd       
  unix  2      [ ]         DGRAM                    10302    1856/smbd           
[/SIZE][/FONT]
I cant figure out where I am missing the clue. Samba works .. on some cases (to a WindowsXP machine on IP, but not on name; to itself on localhostIP but not on name neither on etho IP).
From the WindowsXP machine I dont get a connection at all.
There is no domain involved, names are netbios names.
On the WindowsXP machine a "ping ubuntu" also works ...

Can anybody help me out ?

Greetz, Willy.

---

