---
title: "Game Server not working correctly behind DIR-655 Router"
date: 2010-06-04
forum: Networking &amp; Wireless
---

### Post by xaxtree on 2010-06-04
Well I have no idea if this is the right forum to be posting on but here I go:
I am trying to host a game server or HLDS on my Ubuntu 10.04 PC
I forwarded every necessary port correctly, but every time I try canyouseeme or anything, it says the port isn't open or timed out/not responding.

Help! :(

---

### Post by xaxtree on 2010-06-04
Also, while the server is running, I used the command 
```
sudo netstat -tlnup
```

And the output makes it look like the server is trying to bind to all possible addresses or something?

```

d3adc0d3@xyz:~$ sudo netstat -tlnup
[sudo] password for d3adc0d3: 
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      729/sshd        
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      997/cupsd       
tcp6       0      0 :::22                   :::*                    LISTEN      729/sshd        
tcp6       0      0 ::1:631                 :::*                    LISTEN      997/cupsd       
tcp6       0      0 :::5900                 :::*                    LISTEN      1175/vino-server
udp        0      0 0.0.0.0:39988           0.0.0.0:*                           749/avahi-daemon: r
udp        0      0 0.0.0.0:68              0.0.0.0:*                           1348/dhclient   
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           749/avahi-daemon: r
udp        0      0 192.168.0.192:27015     0.0.0.0:*                           3217/hlds_i686  
udp        0      0 192.168.0.192:26900     0.0.0.0:*                           3217/hlds_i686  
d3adc0d3@xyz:~$ 


```

---

### Post by xaxtree on 2010-06-04
Anyone? :(

---

