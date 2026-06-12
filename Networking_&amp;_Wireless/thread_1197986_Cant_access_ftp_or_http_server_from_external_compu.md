---
title: "Cant access ftp or http server from external computer"
date: 2009-06-26
forum: Networking &amp; Wireless
---

### Post by kehon on 2009-06-26
i have proftpd and lighttpd running and i cant access either on my router i have the ports forwarded but i still cannot connect i've been trying for about 3 hours to get it to work plus some time in the past and i cant get it to work for nothing any ideas would be helpful 

note: i know the servers are running because i can access them both locally but not externally by typing in the ip address i got from whatismyip.com

---

### Post by philcamlin on 2009-06-26
do you have the right ip forworded 

:popcorn:

---

### Post by kehon on 2009-06-26
i forwarded through my dynex router and it forwarded my local ip 192.168.2.3

---

### Post by philcamlin on 2009-06-26
ok do you have apache?

---

### Post by kehon on 2009-06-26
didnt install mainly wanted ftp server and was going to try webserver later

---

### Post by philcamlin on 2009-06-26
install apache

---

### Post by kehon on 2009-06-26
done
sudo apt-get install apache2 (used synaptic though)

still not working

edit: 
tried [http://www.whatsmyip.org/ports/](http://www.whatsmyip.org/ports/)
and tested port 21 (ftp) and it said connection timed out so how do i make sure ports are fowarded correctly

here is my router's (dynex) ports that are forwarded aka virtual servers

[ATTACH]119067[/ATTACH]

did [http://www.canyouseeme.org/](http://www.canyouseeme.org/) port 21 and connection timed out then did
telnet <external ip / ip> 21 and telnet: Unable to connect to remote host: Connection refused

hm i find that i cannot access my servers from another computer connected to the network you have any idea why

---

### Post by kehon on 2009-06-26
i posted earlier about not being able to access either of these (protfpd & lighttpd) from and external computer but i find that i cannot acces it from another computer that is on the same network either all of this stuff the computer server and computer client are on the same network connect by a dynex router

---

### Post by philcamlin on 2009-06-26
port forward...?

your missing something 

do you have a firewall

---

### Post by prshah on 2009-06-26
Your virtual server setup looks fine.

If you have installed lighthttpd there is no need to mess with apache; but now that it is installed, there is no need to remove it either.

You've forwarded the ports in your router; have you opened them up in your firewall?

As a test, drop the firewall, then try to connect. Whatever the result, re-enable the firewall immediately.

If  you are able to connect with the firewall dropped, then you all you need to do is allow the ports in the firewall.

If you are still not able to connect, then clearly the problem lies elsewhere. Are your servers actually running? Is your local IP correct? 

I would also suggest changing "type" in your router to "Both" rather than just TCP.

Commands: From the terminal (Applications-Accessories-Terminal) :

To suspend the firewall ```
sudo ufw disable
```
To enable the firewall ```
sudo ufw enable
```
To allow FTP ports ```
sudo ufw allow 21
```
To allow HTTP ports ```
sudo ufw allow 80
```
To check if FTP/HTTP servers are listening```
netstat -l | grep ":21"
netstat -l | grep ":80"
```

Post back with details on what results you get, for more troubleshooting if required.

---

### Post by kehon on 2009-06-27
i added both and i know they are running and that the local ip is right because i can type in the local ip in firefox and visit it 

netstat hung with the other commands for individual ports so i did this from something else i had tried and it gave this

external ip is correct because i used [www.canyouseeme.org](www.canyouseeme.org) to get it and it says ports are closed too

```
netstat -an | grep "LISTEN "
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp6       0      0 :::6881                 :::*                    LISTEN     
tcp6       0      0 :::139                  :::*                    LISTEN     
tcp6       0      0 :::80                   :::*                    LISTEN     
tcp6       0      0 :::21                   :::*                    LISTEN     
tcp6       0      0 ::1:631                 :::*                    LISTEN     
tcp6       0      0 :::445                  :::*                    LISTEN 
```

---

### Post by Hobgoblin on 2009-06-27
> **kehon said:**
> i posted earlier about not being able to access either of these (protfpd & lighttpd) from and external computer but i find that i cannot acces it from another computer that is on the same network either all of this stuff the computer server and computer client are on the same network connect by a dynex router

Are you trying to use your external IP from within your network?

Most routers are set up to to allow this, the naming of the actual setting to enable it differs from model to model.

---

### Post by kehon on 2009-06-27
> **Hobgoblin said:**
> Are you trying to use your external IP from within your network?

Most routers are set up to to allow this, the naming of the actual setting to enable it differs from model to model.

i tried that and i also went to another computer connected on the same network and tried to use the local ip and it didnt work either

firewall is off, router firewall disabled, servers are running and can check using local ip in browser to see but still can access on another computer on same network and canyouseeme.org says connection timed out leaving me to believe that the port is closed

i at this using sudo su

```
netstat -ntulp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      3090/cupsd      
tcp6       0      0 :::6881                 :::*                    LISTEN      5824/ktorrent   
tcp6       0      0 :::139                  :::*                    LISTEN      2696/smbd       
tcp6       0      0 :::80                   :::*                    LISTEN      23668/lighttpd  
tcp6       0      0 :::21                   :::*                    LISTEN      20480/proftpd: (acc
tcp6       0      0 ::1:631                 :::*                    LISTEN      3090/cupsd      
tcp6       0      0 :::445                  :::*                    LISTEN      2696/smbd       
udp        0      0 0.0.0.0:45192           0.0.0.0:*                           3058/avahi-daemon: 
udp        0      0 192.168.2.3:137         0.0.0.0:*                           2692/nmbd       
udp        0      0 0.0.0.0:137             0.0.0.0:*                           2692/nmbd       
udp        0      0 192.168.2.3:138         0.0.0.0:*                           2692/nmbd       
udp        0      0 0.0.0.0:138             0.0.0.0:*                           2692/nmbd       
udp        0      0 0.0.0.0:68              0.0.0.0:*                           25034/dhclient  
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           3058/avahi-daemon: 
udp        0      0 0.0.0.0:1900            0.0.0.0:*                           5824/ktorrent   
udp6       0      0 :::4444                 :::*                                5824/ktorrent   
udp6       0      0 :::6881                 :::*                                5824/ktorrent   

```

so their running only thing is i cant access them on another computer on network or from internet

---

