---
title: "problem with wine and game server &quot; wont open the ports &quot;"
date: 2013-04-10
forum: Networking &amp; Wireless
---

### Post by murad052 on 2013-04-10
hi

first sorry i have bad english

i have IW5 server .. i  had problem with wine , the server works well i mean by well no error at  all while lunching .. the problem the game doesn't open the ports . for  example i use 27015 and 27016 and 27017 .. non of them is open .

what i did ?


i tried wine 1.2 and 1.3 and 1.4 and 1.5 and same thing

i add the port to /etc/service and iptable .

i setup the server many times and i asked my hosting company if they blocked ports they said NO

i dont know if i miss something or i should setup extra stuff



this is the result of lsof -Pnl +M -i4
> 
COMMAND   PID     USER   FD   TYPE    DEVICE SIZE/OFF NODE NAME
sshd      212        0    3r  IPv4 526044478      0t0  TCP *:22 (LISTEN)
sendmail- 457        0    3u  IPv4 526045508      0t0  TCP 127.0.0.1:25 (LISTEN)
sendmail- 457        0    5u  IPv4 526045509      0t0  TCP 127.0.0.1:587 (LISTEN)
sshd      459        0    3r  IPv4 526045999      0t0  TCP xx.xx.234.37:22->xx.xx.64.202:56198 (ESTABLISHED)
sshd      591        0    3r  IPv4 526048338      0t0  TCP xx.xx.234.37:22->xx.xx.64.202:56200 (ESTABLISHED)
Xvnc4     627        0    0u  IPv4 526064862      0t0  TCP *:6001 (LISTEN)
IW5.exe   870        0   57u  IPv4 526106293      0t0  TCP xx.xx.234.37:60926->176.9.46.228:3025 (ESTABLISHED)
IW5.exe   870        0   60u  IPv4 526103824      0t0  UDP *:35669 
IW5.exe   870        0   61u  IPv4 526103829      0t0  UDP *:27015 
IW5.exe   870        0   62u  IPv4 526104669      0t0  UDP *:27016 
IW5.exe   870        0   67u  IPv4 526106313      0t0  UDP *:27017 
wineserve 873        0  137u  IPv4 526106293      0t0  TCP xx.xx.234.37:60926->176.9.46.228:3025 (ESTABLISHED)
wineserve 873        0  138u  IPv4 526103824      0t0  UDP *:35669 
wineserve 873        0  139u  IPv4 526103829      0t0  UDP *:27015 
wineserve 873        0  140u  IPv4 526104669      0t0  UDP *:27016 
wineserve 873        0  146u  IPv4 526106313      0t0  UDP *:27017

>  iptables -A INPUT -p tcp --dport 27015 -j ACCEPT
root@hghj:~# iptables -A INPUT -p tcp --dport 27016 -j ACCEPT
root@hghj:~# iptables -A INPUT -p tcp --dport 27017 -j ACCEPT
root@hghj:~# iptables -A INPUT -p tcp --dport 8766 -j ACCEPT
root@hghj:~# iptables -A INPUT -p udp --dport 27015 -j ACCEPT
root@hghj:~# iptables -A INPUT -p udp --dport 27016 -j ACCEPT
root@hghj:~# iptables -A INPUT -p udp --dport 27017 -j ACCEPT
root@hghj:~# iptables -A INPUT -p udp --dport 8766 -j ACCEPT




Thanks in advance

---

### Post by murad052 on 2013-04-10
im out of solution please help me

---

### Post by murad052 on 2013-04-11
any suggestion please ... still waiting

---

### Post by Hadaka on 2013-04-11
Hi, you need to port forward those ports in your router.

start port       end port   your computers ip address
27015           27017        192.168.1.8  <-example yours
                                                         will be different.

read your routers manual or do a search on your router
for instructions on port forwarding.
good luck!

---

