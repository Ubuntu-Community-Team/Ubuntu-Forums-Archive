---
title: "Static IP - internet see me, but I cant see internet."
date: 2012-01-04
forum: Networking &amp; Wireless
---

### Post by LimeCut on 2012-01-04
Well. I'm back into using ubuntu. Have tried it before, but i always fall back on windows. But now i have started to mess around with servers. And ubuntu server in commandline = sexy. So I have what i would call a funny problem.
I have just installed ubuntu server 11.10, and i'm going to set up a webserver on it. Or it is already set up, but not configured much yet.
The problem I am experiencing is when i try to give my server a static ip.
So the ip works, and i can access my webserver from the internet checked that it is working by letting a friend of mine check if he got contact with it.

But i havn't got internet connection.
I was going to set up and install an ftp server. The server i was going to download was vsftpd. When i run sudp apt-get install vsftpd, i get this

```

limecut@LimeServ1:~$ sudo apt-get install vsftpd
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  vsftpd
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 117 kB of archives.
After this operation, 463 kB of additional disk space will be used.
Err http://no.archive.ubuntu.com/ubuntu/ oneiric-updates/main vsftpd amd64 2.3.2-3ubuntu5.1
  Temporary failure resolving 'no.archive.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ oneiric-security/main vsftpd amd64 2.3.2-3ubuntu5.1
  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/v/vsftpd/vsftpd_2.3.2-3ubuntu5.1_amd64.deb  Temporary failure resolving 'security.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

This is my interface for my eth cable
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.201
netmask 255.255.255.0
gateway 192.168.1.1

```

also i can ping everything on my network, but i can't ping internet.. at least i don't get any answers.

so.. anyone got a clue what is wrong? i don't get it and havn't touched ubuntu for a year at least!

Thanks in advance
- LC -

---

### Post by sj1410 on 2012-01-04
1) check your /etc/resolv.conf does it have the name servers (DNS) (refer to [configuring dns]("http://blog.swapnil.me/2012/01/configure-linux-as-dns-client.html"))
2) your gateway is 192.168.1.1, if it has a firewall is your ubuntu server allowed access thru it

---

### Post by Grenage on 2012-01-04
**sj1410** is most likely correct, and you're missing DNS server addresses; they are normally given to a machine via DHCP, which you aren't using.

---

### Post by LimeCut on 2012-01-04
My resolv.conf say 
```

nameserver 192.168.1.1

```
And it is ok to use the router as dns, right?


i think my routers firewalls are shut down.. but i'm still running behind another router.. A Jensen router... but all my other machines have no problem connecting to the internet, why should my server not be allowed? sitting behind the same router as my server on this machine. And here i have a static ip just with windows...
i have tried changing the dns, but then all connection is lost.. am i supposed to change the dns in resolv.conf or interface?

---

### Post by sj1410 on 2012-01-04
changing dns in /etc/resolv.conf is a better idea. try 

nameserver 8.8.8.8
nameserver 8.8.4.4

also try pinging 8.8.8.8 if your system is able to reach internet

---

### Post by chili555 on 2012-01-04
> **sj1410 said:**
> changing dns in resolv[COLOR="Red"]e[/COLOR].conf is a better idea. try 

nameserver 8.8.8.8
nameserver 8.8.4.4

also try pining 8.8.8.8 if your system is able to reached internetA typo; he means /etc/resolv.conf.

---

### Post by LimeCut on 2012-01-04
Well. it seems to work now... but i have tried the exact same setup.. must have had an typo somewhere x)
Thx for helping me out here :)

---

