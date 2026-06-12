---
title: "iptables SMTP port translation to other IP"
date: 2011-03-03
forum: Networking &amp; Wireless
---

### Post by luddgopelle on 2011-03-03
Hello.
I have a mail server with a few domains from different providers. I wanted to set the SMTP port to 587, as port 25 is blocked when accessing it from some other networks. One provider could change the incoming mail port for us but not the other, so I am trying to do a port translation from incoming 25 to 587, so it will recieve those mails.

I tried first to do this on the Sonicwall TZ170, a NAT Policy with port translation. I couldn't select either the server or the service in that configuration screen, so I gave up on that.

I then tried with a Ubuntu server next to the mail server (Windows with a mail server program), both located on DMZ, with public IP:s. I could then set UBUNTUSERVER as the mx entry for that domain. 
I tried to use IPTABLES on it to route port 25 packets to the mail server and the new port, like this:
```
sudo iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 25 -j DNAT --to-destination 217.x.xxx.210:587
sudo iptables --list PREROUTING -t nat
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination
DNAT       tcp  --  anywhere             anywhere            tcp dpt:smtp to:217.x.xxx.210:587

```I also tried adding a FORWARD, perhaps that wasn't necessary?```
sudo iptables -A FORWARD -p tcp -i eth0 -d 217.x.xxx.210 --dport 587 -j ACCEPT
```IP forwarding is enabled.
The server wasn't listening to port 25 according to netstat so I installed POSTFIX which added ```
netstat -an
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN

```I don't know if that's "pretty" but I couldn't think of anything else.
However it doesn't seem to work. 
I have tried to Telnet to UBUNTUSERVER 25, expecting to arrive in the mail program via port 587, but it doesn't. Connect failed.
Have I missed something in the PREROUTING?

Anybody know a solution to this? Or a better way? I am not a network or mail expert...
Thanks.

---

