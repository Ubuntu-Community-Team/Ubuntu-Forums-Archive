---
title: "CHeck port forwarding?"
date: 2009-05-06
forum: Networking &amp; Wireless
---

### Post by wesg on 2009-05-06
There are dozens of posts about forwarding ports for various jobs (torrents, mostly) so I'm wondering if anyone can point me in the direction of a tool to test my port forwarding configuration.

Transmission on the Mac has a tool to check if the connection is open, and I'd like to do something similar. Right now I'm seeing much faster speeds on my MacBook than my server, which suggests a network issue. ANy ideas?

---

### Post by waspbr on 2009-05-07
go to system>Admin> network tools > Port scan tab

type the IP of the computer whose port you are trying to forward (check the ip by right clicking the network manager applet and go to Connection information), make some popcorn and grab a beer, and watch the show. 

A list of open ports related to that IP should come up

---

### Post by wesg on 2009-05-07
How might I do this from the command line?

---

### Post by waspbr on 2009-05-08
I did some digging and I found this method, you have to install this small package tho: 

```
sudo apt-get install nmap
```
 

once you install that just type in terminal

```
nmap -v -sT 192.168.0.0/24
```


you just need to replace "192.168.0.0/24" with the IP address of the machine you want to scan, the 0/24 part just adds a range of addresses to scan , in this case it is going to look for all 192.168.0.n for n is all numbers between 0 and 24

I tested this on my machine with the following command

```
nmap -v -sT 192.168.0.8
```

hope this is what you are looking for, if you want to know more about the nmap package, there is a ton of information on this site [http://www.cyberciti.biz/tips/linux-scanning-network-for-open-ports.html]("http://www.cyberciti.biz/tips/linux-scanning-network-for-open-ports.html")

---

### Post by superprash2003 on 2009-05-08
or you could try this [http://www.t1shopper.com/tools/port-scanner/](http://www.t1shopper.com/tools/port-scanner/)

---

