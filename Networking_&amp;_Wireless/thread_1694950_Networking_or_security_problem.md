---
title: "Networking or security problem ?"
date: 2011-02-25
forum: Networking &amp; Wireless
---

### Post by oygle on 2011-02-25
Please see [this post]("http://ubuntuforums.org/showthread.php?t=1693652") , as I'm not 100% convinced that this is a security (firewall) problem.

Could be network, I don't know.   :confused:

---

### Post by oygle on 2011-02-25
I can't ping 'out' to the internet, either by IP or by domain name on the client computer, yet can do 'all' on the gateway.

---

### Post by oygle on 2011-02-25
The only way I could get the client to have access to the internet, was to reboot the gateway computer into Windows XP, .. works fine.

Any way I can check/double check that all the network settings are correct ?

Oygle

---

### Post by oygle on 2011-02-26
The setup is as follows ..

Internet <<==>> ppp0 <> Ubuntu gateway <> eth0 <<==>> Client PC

The gateway computer has the 'share' option enabled, and the client computer has the gateway IP address set in NM. I use NM for both computers.

Gateway computer   192.168.1.100
Client computer    192.168.1.101

Problem - can connect to the internet okay with gateway, but **NOT** client.

Here is the ifconfig from gateway

```

removed per request.

```

Here is the ifconfig from client

```

removed per request

```

I have GUFW installed on both computers, but there is nothing in the logs to suggest a 'block'.

If I restart the network on the gateway, I have to do this again ..

```

sudo ifconfig eth0 192.168.1.100

```

I can also reboot the gateway into Win XP, and that connects okay, **AND** the client _can then connect_.

So is it the Ubuntu gateway or the Ubuntu client that needs some tweaking ?

Oygle

---

### Post by oygle on 2011-02-27
Can UFW/GUFW do ICS  ??

---

### Post by oygle on 2011-02-27
I still can't access the internet from the client computer.  :(

---

### Post by oygle on 2011-02-27
Anyone ??

---

### Post by dmizer on 2011-02-28
Closing this, as it is a duplicate. If you want a post moved, please use the "report abuse" link and ask for it to be moved.

I will move your other thread to the networking form, as what you want to do is a networking issue.

---

