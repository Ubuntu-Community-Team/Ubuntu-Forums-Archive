---
title: "port forwarding"
date: 2010-04-14
forum: Networking &amp; Wireless
---

### Post by fabiett0 on 2010-04-14
I have a small server with static ip and a IPCAM (axis 205 network camera) (192.168.123.10) that use the  port 1130.


<web> ==eth0==MYSERVER==ETH1== IPCAM 


My goal is to see the webcams from internet: 

[http://MY_STATIC_IP:1130](http://MY_STATIC_IP:1130)



:lolflag:


my ufw before rules is [http://pastebin.com/8fycfd8d](http://pastebin.com/8fycfd8d)

and my ufw status is 

xxxx@BatServer:~$ sudo ufw status
Status: active

To                         Action      From
--                         ------      ----
22/tcp                     ALLOW       Anywhere
80                         ALLOW       Anywhere
631                        ALLOW       Anywhere
54925/udp                  ALLOW       Anywhere
1130/tcp                   ALLOW       Anywhere
150.217.48.217 1130/tcp    ALLOW       Anywhere


i can see the webcam [http://MYSTATICIP:1130](http://MYSTATICIP:1130) from my LANif I use the command

sudo iptables -t nat -A PREROUTING -d MYSTATICIP -p tcp --dport 1130 -j DNAT --to-destination 192.168.123.10:1130


but it is unreachable from the  outside.... :confused:


Can you help please?

:guitar:

---

### Post by 98cwitr on 2010-04-14
can you ping your external ip from the outside? How is your router (ie: firewall) setup? is your setting listed in iptables?

---

### Post by fabiett0 on 2010-04-14
i can ping my site, and work perfectly

my iptables -L is [http://pastebin.com/P36Nk6Fq](http://pastebin.com/P36Nk6Fq)

---

### Post by 98cwitr on 2010-04-14
and your static IP is an outside address? You can access the camera internally?

---

### Post by fabiett0 on 2010-04-14
All People into the LAN can see the camera output...

but All people outside this LAN can't see the camera output

---

### Post by 98cwitr on 2010-04-14
outside static address on the machine?

---

### Post by fabiett0 on 2010-04-14
outside with static address?

connection time-out :(

---

### Post by gordintoronto on 2010-04-14
What router are you using?

What is the machine's IP address?

---

### Post by fabiett0 on 2010-04-14
My server with Static Ip, is a DHCP server and have 2 ip

eth0 with public ip pingu.pin.unifi.it

and eth1 192.168.123.1

my webcam have 192.168.123.10:1130

---

### Post by fabiett0 on 2010-04-15
with this rule 

sudo iptables -t nat -A PREROUTING -p tcp --dport 1130 -d MYSTATICIP -j DNAT --to-destination 192.168.123.10:1130

we can see the webcam from the LAN... :(

---

