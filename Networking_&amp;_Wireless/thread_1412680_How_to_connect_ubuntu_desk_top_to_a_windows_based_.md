---
title: "How to connect ubuntu desk top to a windows based server at work."
date: 2010-02-21
forum: Networking &amp; Wireless
---

### Post by Billieboi on 2010-02-21
I need help on how to connect my newly installed ubuntu on my desktop at work to the company's server that is windows based. I have my user name and password given to me by my it office but they could not help me set up linux. Plz help

---

### Post by Iowan on 2010-02-21
A few more details: Is machine set for (should it get) a DHCP address? Does it get one? (**ifconfig -a**)

---

### Post by bcbc on 2010-02-22
I can either VPN in and access shares, or login directly with remote desktop. What exactly are you trying to do?

---

### Post by Billieboi on 2010-02-22
> **Iowan said:**
> A few more details: Is machine set for (should it get) a DHCP address? Does it get one? (**ifconfig -a**)

I don't know. I'm not sure whats a DHCP address. fairly new with this. I did cut and paste what you wrote to the terminal and got this:

will@will:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:13:72:af:87:f0  
          inet addr:192.168.16.144  Bcast:192.168.16.255  Mask:255.255.255.0
          inet6 addr: fe80::213:72ff:feaf:87f0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:436503 errors:0 dropped:0 overruns:0 frame:0
          TX packets:109412 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:93629151 (93.6 MB)  TX bytes:18697845 (18.6 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1552 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1552 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:113942 (113.9 KB)  TX bytes:113942 (113.9 KB)

---

### Post by Billieboi on 2010-02-22
> **bcbc said:**
> I can either VPN in and access shares, or login directly with remote desktop. What exactly are you trying to do?

I would like to turn my desktop on, put my username and password thats in the network, and be on line with access to my email, printing etc. through my company's server.

---

### Post by Iowan on 2010-02-22
Well, it appears that the machine has an IP address - good start...
[This]("http://ubuntuforums.org/showthread.php?t=1169149") thread might help with accessing Windows shares. Email might be a trick...

---

### Post by bcbc on 2010-02-25
If you're on the same network you should be able to connect to the share. I used "Places", "Connect to Server", For Service type. select 'Windows Share'.
Then enter server name/ip, share name, userid, and domain - add a bookmark to reconnect easily. And that's it.

You'll need to get your server name/ip and the share names from your network administrator.
If you are not on the same LAN you'll probably have to connect using VPN before it will allow you to access the shares.

For email, I assume you just need the mail server name and type (imap/pop/exchange whatever) and then plug in your userid and password. Your network administrator should be able to assist you on this. Same deal as for shares - unless the server is internet facing, you'll need to be on the LAN or VPN in.

I don't use a local email client on Ubuntu, but I do use VPN to connect to shares on a windows server as described above.

---

### Post by Billieboi on 2010-03-01
> **bcbc said:**
> If you're on the same network you should be able to connect to the share. I used "Places", "Connect to Server", For Service type. select 'Windows Share'.
Then enter server name/ip, share name, userid, and domain - add a bookmark to reconnect easily. And that's it.

You'll need to get your server name/ip and the share names from your network administrator.
If you are not on the same LAN you'll probably have to connect using VPN before it will allow you to access the shares.

For email, I assume you just need the mail server name and type (imap/pop/exchange whatever) and then plug in your userid and password. Your network administrator should be able to assist you on this. Same deal as for shares - unless the server is internet facing, you'll need to be on the LAN or VPN in.

I don't use a local email client on Ubuntu, but I do use VPN to connect to shares on a windows server as described above.




Thanks soo much for your help.

---

### Post by bcbc on 2010-03-01
You're welcome :)

---

