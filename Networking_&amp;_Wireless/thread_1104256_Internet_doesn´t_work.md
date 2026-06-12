---
title: "Internet doesn´t work"
date: 2009-03-23
forum: Networking &amp; Wireless
---

### Post by ubles on 2009-03-23
Hi, i`ve four PCs on a Lan. Three of them have windows OS and one has ubuntu. The problem is that windows pcs have internet conection, but ubuntu doesn`t. The pcs can shared files without problems. I mean, the lan works fine, but internet doesn`t work from ubuntu. When i try ping [www.google.com](www.google.com) i get the message:

ping [www.1.google.com](www.1.google.com) (XX.XXX.XX.XXX) 56(84) bytes of data

..Then there is no response, and if i cancel the command i get: 100% packet lost.

Any Help Will be appreciated.
Thanks and sorry for my english

---

### Post by jelle_ on 2009-03-23
can you sent me the output of traceroute?  you can download it from: 
[http://mirrors.kernel.org/ubuntu/pool/main/t/traceroute/traceroute_2.0.11-2_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/t/traceroute/traceroute_2.0.11-2_i386.deb)

usage: traceroute [www.google.com](www.google.com)

---

### Post by kestrel1 on 2009-03-23
Can you post the output from```
ifconfig
```

---

### Post by ubles on 2009-03-23
traceroute [www.google.com](www.google.com)
traceroute [www.google.com](www.google.com) (XXX.XXX.XXX.XXX), ....
1 * * *
2 * * *
....

The same configuration on a windows pcs works fine, but in ubuntu i don`t have access to internet.

---

### Post by ubles on 2009-03-23
ifconfig

eth7 Link encap:Ehternet HWaddr 08:00:25....
     inet addr: 192.168.1.168 Bcast 192.168.3.255 mask 255.255.252.0
...
...
lo ....
...
...
...

you need the complete output?

---

### Post by kestrel1 on 2009-03-23
What is the typical output from a windows machine with```
ipconfig /all
```
Just trying to make sure you are using the same ip range & subnet mask.
I suspect you are if you can share files over the lan.

edit: you aren't behind a proxy server by any chance?

---

### Post by ubles on 2009-03-23
I'm behind a proxy server, but i can`t modify any configuration. This proxy is the default gateway in windows and ubuntu.

I try the same configuration on windows xp and ubuntu (same ip netmask and gateway), in windows xp works but in ubuntu doesn´t.

the ipconfig output is:

...
ip: 192.168.1.168
netmask: 255.255.252.0
gateway: 192.168.1.254
...

Thanks

---

### Post by kestrel1 on 2009-03-23
Have you set the network proxy config in Ubuntu under: System -> Preferences -> Network Proxy & set Firefox to use the system proxy or to use the proxy.

---

### Post by ubles on 2009-03-23
i`m only using the console... I've not installed any graphic interface.... So I realize that internet doesn`t work when i try ping or try to install a package/application....

Thanks

---

### Post by ubles on 2009-03-25
I`ve tried to change ips but still doesn´t works....The same configuration in windows works. I don`t know if the problem is in Ubuntu or in the LAN.

Any help please!!!!

Thanks

---

### Post by markdjones82 on 2009-03-25
Try setting your environment variable 

$http_proxy=proxyaddress

wget [www.google.com](www.google.com)

if it downloads it works.

To set it permanent set it in your ~./profile

---

### Post by kestrel1 on 2009-03-25
Are you able to ping gateway & router.

---

### Post by markdjones82 on 2009-03-25
Also check your DNS settings and see if anything is in there:

/etc/resolv.conf

Try this link for more troubleshooting:

[http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html](http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html)

Sometimes with DHCP and proxy servers ubuntu doesn't pick up a DNS server.  This can cause it not to know what the address is.  See if you can ping a websites IP address

---

### Post by shunyata on 2009-06-18
Dude I had a similar issue and I have 2 windows machines and 1 running ubuntu 9.04 jaunty jackalope.  I spent a whole day doing the usual thing, you find on the internet and in the forums.  You know what fixed it?  I deleted the network connection known as "wired connection 1" , this is a windows networking trick , and I decided to try it when the other solutions were getting to convoluted and getting me no where. Guess what when I created another connection , and put the hardware "mac address" when creating a new connection that brought the connection right up.  Whew whooooo!  Cool.\\:D/

---

