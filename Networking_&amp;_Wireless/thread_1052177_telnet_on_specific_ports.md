---
title: "telnet on specific ports"
date: 2009-01-27
forum: Networking &amp; Wireless
---

### Post by commandos on 2009-01-27
Hello ,

i'm running a service which use xx port , i want other to be able to telnet on that port .

when i run this cmd line i get the followings :  

netstat -l -n



tcp        0      0 127.0.0.1:6082          0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:389             0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN
[COLOR="Red"]tcp        0      0 127.0.0.1:88            0.0.0.0:* [/COLOR]              LISTEN
[COLOR="DarkGreen"]tcp6       0      0 :::389                  :::*                    LISTEN
tcp6       0      0 :::5800                 :::*                    LISTEN
tcp6       0      0 :::8009                 :::*                    LISTEN
tcp6       0      0 :::5900                 :::*                    LISTEN
tcp6       0      0 :::8180                 :::*                    LISTEN
tcp6       0      0 :::22                   :::*                    LISTEN
tcp6       0      0 :::8123                 :::*                    LISTEN[/COLOR]
udp        0      0 0.0.0.0:32769           0.0.0.0:*
udp        0      0 0.0.0.0:68              0.0.0.0:*
udp        0      0 0.0.0.0:5353            0.0.0.0:*


the other machine on the network are only able to telnet on the port (389,5800,8009 5900,8180,22 and 8123)


is there a cmd line that i can write to allow the telnet option on port 88 (where my service is running) ...

---

