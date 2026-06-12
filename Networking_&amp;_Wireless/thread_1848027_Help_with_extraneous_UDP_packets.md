---
title: "Help with extraneous UDP packets"
date: 2011-09-21
forum: Networking &amp; Wireless
---

### Post by lobo_tuerto on 2011-09-21
Hello guys,


I'm new in respect of networking, I have a fresh Ubuntu install, with all upgrades in.

After installing **iptraf** I noticed that every once in a while (like every few secs, or something, even using netstat) this would appear in the bottom pane of **iptraf**:

```
UDP (44 bytes) from 127.0.0.1:32953 to 127.0.0.1:32953 on lo
UDP (44 bytes) from 127.0.0.1:32953 to 127.0.0.1:32953 on lo
UDP (52 bytes) from 127.0.0.1:32953 to 127.0.0.1:32953 on lo
UDP (52 bytes) from 127.0.0.1:32953 to 127.0.0.1:32953 on lo
UDP (44 bytes) from 127.0.0.1:32953 to 127.0.0.1:32953 on lo
UDP (44 bytes) from 127.0.0.1:32953 to 127.0.0.1:32953 on lo
UDP (340 bytes) from 127.0.0.1:32953 to 127.0.0.1:32953 on lo
UDP (340 bytes) from 127.0.0.1:32953 to 127.0.0.1:32953 on lo
UDP (244 bytes) from 127.0.0.1:32953 to 127.0.0.1:32953 on lo
UDP (244 bytes) from 127.0.0.1:32953 to 127.0.0.1:32953 on lo
```

They appear in a rapid succession, then stop just to start again after some time has elapsed (time is generally not a whole minute).


I decided to check what program was doing this with netstat, only to get this:
```
$ sudo netstat -u
Conexiones activas de Internet (servidores w/o)
Proto  Recib Enviad Dirección local         Dirección remota       Estado      
udp        0      0 localhost:32953         localhost:32953         ESTABLECIDO
```


Can anyone shed some light on this please?

---

### Post by lobo_tuerto on 2011-09-23
Yeah, turned out that the program doing it was the postgresql server.

You can see who is connected to what port with this command:
```
sudo netstat -utnp | grep 32953
```

Best regards,
Me.

---

