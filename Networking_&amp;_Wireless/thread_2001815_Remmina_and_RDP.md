---
title: "Remmina and RDP"
date: 2012-06-11
forum: Networking &amp; Wireless
---

### Post by ttoolin on 2012-06-11
I am using almost clean installs of ubuntu 12.04 on two machines.  T am trying to get RDP to work, using Remmina.  I plan on adding a Windows computer to the mix, later.

VNC  works fine.  RDP doesn't work at all - just 'unable to connect'.

Thescarce instructions I can find suggest this is no-hassle, so it seems like I just need to toggle some setting the other way, or something simple like that.

Please help.

Thanks.

---

### Post by Locus Kiesselbachi on 2013-04-11
bump

(L)ubunut 12.10

---

### Post by steeldriver on 2013-04-11
On the server side, you can

1. make sure the xrdp / sessman services are running

```
$ service xrdp status
 * Checking status of Remote Desktop Protocol server xrdp                                                                                                                   [ OK ] 
 * Checking status of RDP Session Manager sesman                                                                                                                            [ OK ] 
```

2. use netstat to check the services are bound to the expected ports

```
$ sudo netstat -nlpt | grep xrdp
tcp        0      0 127.0.0.1:3350          0.0.0.0:*               LISTEN      3995/xrdp-sesman
tcp        0      0 0.0.0.0:3389            0.0.0.0:*               LISTEN      3993/xrdp     
```

3. check whether the server side firewall is enabled and if so whether it is allowing incoming connections for those ports

```
$ sudo ufw status
Status: active

To                         Action      From
--                         ------      ----
22/tcp                     ALLOW       192.168.1.0/24
3389/tcp                   ALLOW       192.168.1.0/24
3350/tcp                   ALLOW       192.168.1.0/24
```

On the client side you can use telnet or nmap to make sure the port is reachable

```
$ telnet 192.168.1.12 3389
Trying 192.168.1.12...
Connected to 192.168.1.12.
Escape character is '^]'.
^]


$ sudo nmap -p 3389 192.168.1.12

Starting Nmap 5.21 ( http://nmap.org ) at 2013-04-11 17:19 UTC
Nmap scan report for 192.168.1.12
Host is up (0.022s latency).
PORT     STATE SERVICE
3389/tcp open  ms-term-serv
MAC Address: XX:XX:XX:XX:XX:XX (Intel Corporate)

Nmap done: 1 IP address (1 host up) scanned in 0.11 seconds
```

---

### Post by Locus Kiesselbachi on 2013-04-11
Thnx for fast replay to start with.
Oncle Google this time didnt understand my question -thats why I bumped this thread.

I add that, in win7 "Remote desktop" connects server (work). So server is up and running - no problems at all.
I made update to (L)ubuntu, but it didnt change any better, only some problems. Im going to reinstall OS, it can take some time to make this (also all the "apt-get install") and to troubleshoot rooting/connection problems.
I add that Remmina can identify server (i think?), because it gives me server certificate, which I dont know how to interpretate (I remember it had "fingerprint:").

---

### Post by steeldriver on 2013-04-11
> **Locus Kiesselbachi said:**
> it gives me server certificate, which I dont know how to interpretate (I remember it had "fingerprint:").

Have you got it set up to use SSH tunneling by any chance? it sounds like the server is presenting its host cert and asking if you want to add it to your known_hosts file

---

### Post by Locus Kiesselbachi on 2013-04-11
```
service xrdp status
```
**gives:**
xrdp: unrecognized service

:-k

```
sudo netstat -nlpt | grep xrdp
```
**gives:**
nothing...
:neutral:

should I continue?

edit:
Thats interesting. I have another older rig, that has Lubuntu 11.10 on it at it has no problems at all connecting with Remmina GUI.

edit 2 **[SOLVED]**:
This what resolved my problem: [here]("http://askubuntu.com/questions/157723/cannot-rdp-to-windows-7-with-remmina-on-12-04") (Right click, Edit ...[COLOR=#333333][FONT=Ubuntu Beta]Click Advanced tab in your Remote Desktop Preferences and choose RDP in Security drop down menu and save.)[/FONT][/COLOR]

I must say that before that I did also
```
[COLOR=#333333]sudo apt-get install xrdp[/COLOR]
```




:guitar:

---

