---
title: "SSH problems through the web"
date: 2011-08-21
forum: Networking &amp; Wireless
---

### Post by bholzer on 2011-08-21
So I've been using SSH for a while, but only to connect to machines on my network. The problems start when I try to connect from somewhere else!

I have set up port forwarding on my router. I have ssh connections on port 22 set to forward to 192.168.1.138

That machine is a Mac, and the user is stephanie. On my network, I connect with stephanie@192.168.1.138(duh, that's the easy part).

NOW, I'm trying to connect from a different network like so: [email]stephanie@XXX.XXX.XXX.XXX[/email]<- This of course being my IP. What should (I think?) happen, is the connection is recognized as SSH, therefore forwarded to the machine I specified.

One of two things happens here:
1. I get a timed-out error or

2. It asks me for a password. I have keys on the two machines, so I usually have a password-free connection. If it asks for the password, I enter what the password would be, and it tells me access denied. 

Where am I going wrong here?

---

### Post by lmarmisa on 2011-08-22
> **bholzer said:**
> So I've been using SSH for a while, but only to connect to machines on my network. The problems start when I try to connect from somewhere else!

I have set up port forwarding on my router. I have ssh connections on port 22 set to forward to 192.168.1.138

That machine is a Mac, and the user is stephanie. On my network, I connect with stephanie@192.168.1.138(duh, that's the easy part).

NOW, I'm trying to connect from a different network like so: [EMAIL="stephanie@XXX.XXX.XXX.XXX"]stephanie@XXX.XXX.XXX.XXX[/EMAIL]<- This of course being my IP. What should (I think?) happen, is the connection is recognized as SSH, therefore forwarded to the machine I specified.

One of two things happens here:
1. I get a timed-out error or

2. It asks me for a password. I have keys on the two machines, so I usually have a password-free connection. If it asks for the password, I enter what the password would be, and it tells me access denied. 

Where am I going wrong here?

Do you get a message like this?

```

Permission denied, please try again.

```I get the previous message if I type an incorrect password.

Do you get a message telling "access denied"?.

---

### Post by bholzer on 2011-08-22
> **lmarmisa said:**
> Do you get a message like this?

```

Permission denied, please try again.

```I get the previous message if I type an incorrect password.

Do you get a message telling "access denied"?.

I do. But I know I'm putting the correct password in, and I shouldn't even have to use the password, as I'm using keys. Or am I completely mistaken?

---

### Post by papibe on 2011-08-22
How do you get your public IP (the one represented by the Xs)?

From where are you failing to connect to your network?

Regards.

---

### Post by lmarmisa on 2011-08-22
I do not know if the ssh server configuration of your Mac machine is different from Linux-Ubuntu.

Are you using a file named **/etc/ssh/ssh_known_hosts **in your Mac host machine?.

A different question: do you receive email messages of your thread subscriptions?. They stopped here two days ago.

---

### Post by bholzer on 2011-08-22
> **papibe said:**
> How do you get your public IP (the one represented by the Xs)?

From where are you failing to connect to your network?

Regards.

I'm getting my public IP from whatismyip.com

I've only tried from two different networks aside from my own. It didn't work from any of the three.

> **lmarmisa said:**
> 
I do not know if the ssh server configuration of your Mac machine is different from Linux-Ubuntu.

Are you using a file named /etc/ssh/ssh_known_hosts in your Mac host machine?.

A different question: do you receive email messages of your thread subscriptions?. They stopped here two days ago.

I'm using ~/.ssh/authorized_keys in the host.

I do not get emails, so I can't help there, sorry!

---

### Post by papibe on 2011-08-22
A few tips:
[LIST]
[*] You have to set your machine with an static LAN IP or use DHCP reservation (usually configurable on the router).
[*]In order to connect to your machine using your public IP, you have to do it from outside. A public library, an Internet cafe, or better a friend's house. Another alternative is us your phone using the carrier service (not WiFi). What happens here is that most routers don't have the functionality to deal with that kind of requests (it is called [NAT Loopback]("http://www.dyndns.com/support/kb/loopback_connections.html")).
[*]Most ISPs give you a dynamic public IP that varies from time to time. If you haven't checked whatismyip.com recently, you maybe trying to connect to a different house!  This won't be an issue if you have an static IP (usually a more expensive service).
[*]An easy way to work with dynamic IPs is to subscribe to a dynamic dns service. I use DynDNS (free). For Ubuntu the client is in the repositories, and it's called ddclient (look in their site for more versions).
[*]There are a couple of files that can be blocking the connection. Post them here is you have them:
```
/etc/hosts.equiv
/etc/ssh/shosts.equiv
~/.rhosts

```
Although the easy way to take them out of the equation is to set the option 'IgnoreRhosts yes' in your sshd config file (usually  ls /etc/ssh/sshd_config)
[/LIST]
I hope it helps,
Regards.

---

### Post by lmarmisa on 2011-08-22
If the public key of the client is included in the file **authorized_keys** of the server you will be not asked for any password. This is an example:

```

luis@UB1010ENG:~/.ssh$ ssh luis@ub1104zotac
The authenticity of host 'ub1104zotac (192.168.2.61)' can't be established.
RSA key fingerprint is af:41:1c:68:38:9a:b7:a6:71:01:28:6f:51:43:d0:8d.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'ub1104zotac,192.168.2.61' (RSA) to the list of known hosts.
Welcome to Ubuntu 11.04 (GNU/Linux 2.6.38-10-generic i686)

 * Documentation:  https://help.ubuntu.com/

Last login: Mon Aug 22 07:51:54 2011 from localhost
luis@UB1104ZOTAC:~$


```Now I am going to remove the public key of the client in the file **authorized_keys** of the server.

In this case, the server asks for password:

```

luis@UB1010ENG:~/.ssh$ ssh luis@ub1104zotac
The authenticity of host 'ub1104zotac (192.168.2.61)' can't be established.
RSA key fingerprint is af:41:1c:68:38:9a:b7:a6:71:01:28:6f:51:43:d0:8d.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'ub1104zotac,192.168.2.61' (RSA) to the list of known hosts.
[COLOR=Blue]luis@ub1104zotac[/COLOR]'s password: 
Welcome to Ubuntu 11.04 (GNU/Linux 2.6.38-10-generic i686)

 * Documentation:  https://help.ubuntu.com/

Last login: Mon Aug 22 08:19:17 2011 from ub1010eng
luis@UB1104ZOTAC:~$

```Maybe you are trying to connect to a different ssh server than your Mac machine. This is the reason because you are not authorized and, therefore, the server asks for a password. You give the password but this password belongs to an account of other machine. This could explain your problem. Do you have more ssh servers on your LAN?. Do you know if the UPnP protocol in enabled in your router?.

NOTE: I removed the file **know_hosts **on the server before to type the two commands **ssh**.

---

### Post by bholzer on 2011-08-23
> **lmarmisa said:**
> Maybe you are trying to connect to a different ssh server than your Mac machine. This is the reason because you are not authorized and, therefore, the server asks for a password. You give the password but this password belongs to an account of other machine. This could explain your problem. Do you have more ssh servers on your LAN?. Do you know if the UPnP protocol in enabled in your router?.

NOTE: I removed the file **know_hosts **on the server before to type the two commands **ssh**.
I have two ssh servers, I ssh regularly to the Mac, and to another Ubuntu host.

I do not know about the UPnP. What difference does it make?

---

### Post by lmarmisa on 2011-08-23
> **bholzer said:**
> I have two ssh servers, I ssh regularly to the Mac, and to another Ubuntu host.

I do not know about the UPnP. What difference does it make?

If the UPnP feature is enabled, another SSH server could (potentially) to set automatically the port forwarding over port 22:

[INDENT]*[The Universal Plug and Play protocol (UPnP)]("http://en.wikipedia.org/wiki/Port_forwarding") provides a feature to automatically install instances of port forwarding in residential Internet gateways. UPnP defines the Internet Gateway Device Protocol (IGD) which is a network service by which an Internet gateway advertises its presence on a private network via the Simple Service Discovery Protocol (SSDP). An application that provides an Internet-based service may discover such gateways and use the UPnP IGD protocol to reserve a port number on the gateway and cause the gateway to forward packets to its listening socket.*[/INDENT]

This is only a supposition. Personally, I doubt that UPnP will be the origin of your problem.

Anyway check if you are really being connected to the other ssh server when you access remotely. Try to connect to [email]your_account_in_ubuntu_ssh_host@XXX.XXX.XXX.XXX[/email].

---

