---
title: "trying to build a router, please help ..."
date: 2012-06-20
forum: Networking &amp; Wireless
---

### Post by 32smooth on 2012-06-20
Hello fellas,

i'm new to ubuntu and i'm trying to build a router. 
My current setup: internet connection comes wireless via LTE. I'm using the hardware that came from my ISP: an LTE modem which is connected via ethernet to a router (vodafone easybox). I want to replace that router with a Linux driven PC. Thanks to another guy who found out how to communicate with the LTE modem I'm able to speak to the modem and get it to 'dial in' to the ISP. The modem has no IP but listens on 3 virtual lans, one for controlling the modem, one for the internet connection and one for SIP telephony (I dont care for the telephony part atm).
So i got that running. I can telnet to the modem, send AT commands and make it dial in.
Then I go and request my dynamic IP, i simply do an dhclient eth1.132 (the virtual lan interface für the internet connection). I get the IP, the default route is set and the resolv.conf gets updated. All seems fine. I can even ping other hosts without problems. Now the strange part: some sorts of connections work, others do not. I can log into an ftp server, provide my credentials, but cannot download a file. It tries, but not a single bit will be received. Same with HTTP. On the other hand i can open an ssh connection to an outside server and use it just fine, no problems at all ...
I dont get it ... i flushed all firewall rules and really have no idea whats going on ...

maybe some experts here can give me a hint ...

many thanks in advance,
 32smooth

---

### Post by poolet on 2012-06-20
> **32smooth said:**
> Hello fellas,

i'm new to ubuntu and i'm trying to build a router. 
My current setup: internet connection comes wireless via LTE. I'm using the hardware that came from my ISP: an LTE modem which is connected via ethernet to a router (vodafone easybox). I want to replace that router with a Linux driven PC. Thanks to another guy who found out how to communicate with the LTE modem I'm able to speak to the modem and get it to 'dial in' to the ISP. The modem has no IP but listens on 3 virtual lans, one for controlling the modem, one for the internet connection and one for SIP telephony (I dont care for the telephony part atm).
So i got that running. I can telnet to the modem, send AT commands and make it dial in.
Then I go and request my dynamic IP, i simply do an dhclient eth1.132 (the virtual lan interface für the internet connection). I get the IP, the default route is set and the resolv.conf gets updated. All seems fine. I can even ping other hosts without problems. Now the strange part: some sorts of connections work, others do not. I can log into an ftp server, provide my credentials, but cannot download a file. It tries, but not a single bit will be received. Same with HTTP. On the other hand i can open an ssh connection to an outside server and use it just fine, no problems at all ...
I dont get it ... i flushed all firewall rules and really have no idea whats going on ...

maybe some experts here can give me a hint ...

many thanks in advance,
 32smooth


:) Hello, check your ports of :21 :22 :80 & :8080 if are open... the same for your machine, 

```
sudo apt-get install nmap 
```end then 
```
nmap -A "ip range - 192.168.0.1" -p "port you want to check 8080"
```at the end try to flush dns of your machine since your SIP is working 
may occurs other services!! 

```
sudo /etc/init.d/nscd restart
```

---

### Post by rukiaEnix on 2012-06-20
When you say that you can't download a file. Are you talking about downloading it with FTP?

---

### Post by 32smooth on 2012-06-21
Hello poolet and rukiaEnix,

thanks for the answers. 

@poolet: 
I'll check the open ports when i'm home (i'm at work now). But I'm rather sceptical that this is the cause of my problems. I'm not using the SIP connection that is provided by the ISP at the moment. The servers that I want to access are normal public webservers, ftpservers and so on, so their ports are open and I flushed the firewall rules on my router. All i want to archive is a simple internet connection.

@rukiaEnix:
yes, but that is only one example of the connections that fail. I cannot access any public webserver as well. I can ping other (outisde) hosts, i can successfully open ssh connections to other (outside) servers. But i cannot access simple webservers. I can open ftp connections, the login process works but downloading a file doesn't ... its strange and I dont know what to do ...

So .. DNS works, SSH works, FTP works partly, Websurfing doesn't work ... what the heck is that? i'm lost ...

---

### Post by rukiaEnix on 2012-06-21
OK, you should check if your modem and router are blocking http ports to the outside.

---

### Post by 32smooth on 2012-06-21
ok i found a solution: using another NIC made it work. I dont know why. So far i used n pcmcia NICfrom Intel, now im using the internal NIC (Intel as well). And this works ... *shrugs*

---

