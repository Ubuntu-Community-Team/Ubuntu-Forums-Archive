---
title: "2 ethernet and cups"
date: 2010-09-03
forum: Networking &amp; Wireless
---

### Post by newton_9 on 2010-09-03
Hello

I am new to Ubuntu and need urgent help.. what i m trying to do is following

In my machine there are 2 ethernet cards eth0 and eth1. The eth0 is DHCP enabled and got IP automatically. At eth1, i want to attach a TCP/IP direct Printer. CUPS is already installed in the system. I want to make the system as PRINT SERVER. the client request comes through eth0 and forward to eth1 attached printer.

ifconfig: eth0 is
ip: 192.168.16.19
broadcast: 192.168.255.255
netmask: 255.255.0.0
gateway 192.168.0.1

1st question is... what could be network setting for eth1?
NOTE: THE PRINTER IP IS 192.168.16.43.. which is attach to eth1

How i route print request from eth0 to eth1?

do cups support? what i am trying to achive.

I an anxiously waiting reply for the community

---

### Post by newton_9 on 2010-09-03
Anybody there?

---

### Post by BkkBonanza on 2010-09-03
Is there a reason you want to put the printer on it's own interface? Usually you would just attach the printer to a switch/router port and then access it using it's IP from anywhere on the LAN.

If you must have it on a dedicated interface then you will need a route command something along this lines,

route add -net 192.168.16.43 netmask 255.255.255.255 dev eth1

Where this IP matches the one for your eth1 interface. This tells it to route packets for this IP to that interface. But also for other machines on the LAN they need to know to route packets for this IP to this machine. That would generally be handled by the router unless this machine is also your gateway.

...
btw you shouldn't bump your post more than once within 24 hours.

---

### Post by newton_9 on 2010-09-06
what i understood is to add this route command

route add -net 192.168.16.43 netmask 255.255.255.255 dev eth1

eth1 interface might be like that

ifconfig eth1 192.168.16.43 netmask 255.255.0.0

or i need to change eth1 IP to something different?

I am still not able to access that printer from cleints. do i need to make that machine as GATEWAY? How could i make that machine as gateway when there are 2 interfaces? with different IP

thanks in advance

---

### Post by BkkBonanza on 2010-09-06
I don't know all the details of your LAN and how you've set things up, like DHCP and other routes etc.

You need to let the network know how to get to that printer because you've gone and stuck it on it's own interface. Your machine is listening on 192.168.16.19 - it's not going to get packets for 192.168.16.43 - it will ignore them. So you will need to add another route in your gateway machine to tell it to handle that IP by sending it to 192.168.16.19 as gateway.

On your gateway machine (192.168.0.1),

sudo route add -net 192.168.16.43 netmask 255.255.255.255 gw 192.168.16.19

That gets packets over to the right machine. But once there it needs to route them across to the other interface.

On the machine the printer hangs off (192.168.16.19),

sudo route add -net 192.168.16.43 netmask 255.255.255.255 dev eth1

This says send them to that interface. As long as your printer has the right IP it should get them.

On this machine you will also need to enable forwarding, and probably add an iptables forwarding rule - though I'm not sure about that.

echo 1 > /proc/sys/net/ipv4/ip_forward

All this needs to be done upon booting each time. So you'll need an init script linked into the booting process on each machine.

(BTW If you just plug the printer into a switch along with the rest of the machines on your LAN then you don't have to do any of this.)

---

### Post by newton_9 on 2010-09-06
Thanks BkkBonaza. very kind of u

I m trying to make that machine as print server, which can hold print jobs and only admin could print them, and in that scenario printer is located right next to his machine. 

I don't want to change any configuration on GW 192.168.0.1 

So after a lot more google i came to conclude BRIGING might be best solution. what i did is as followed, may be u can make me correct or it might benificial for ther users

ifconfig eth0 down
ifconfig eth1 down

ifconfig eth0 0.0.0.0 // DHCP 

// created dummy network for briging
ifconfig eth1 10.10.0.10 netmask 255.255.255.255

brctl addbr mybridge
brctl addif mybridge eth0
brctl addif mybridge eth1

// assign brige same IP as eth0 got
ifconfig mybridge 192.168.16.19 netmask 255.255.0.0

// for internet to work on
route add default gw 192.168.0.1

So now, i m managed to PING 192.168.16.19 and printer IP 192.168.16.43 from any client on network and also printed test page

Any improvement BkkBonaza?

---

### Post by BkkBonanza on 2010-09-06
Yes, that will work. 
It's a good idea since you don't need to keep the segments separate anyway.

You will want to add that config into the /etc/networking/interfaces file so that it gets set on booting. Follow the correct format - you can likely find an example online of a bridge cfg in this file.

A bridge is the same thing as a switch. What you did is turn your two interfaces into a "switch" instead. Which is the easy way to hook up.

---

