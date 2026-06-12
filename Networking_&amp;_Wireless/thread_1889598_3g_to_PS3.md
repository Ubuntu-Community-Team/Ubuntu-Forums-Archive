---
title: "3g to PS3?"
date: 2011-12-01
forum: Networking &amp; Wireless
---

### Post by joi_gudni on 2011-12-01
Hey people,

I have Ubuntu 04.11 or something like that in my Asus Eee-7000 laptop, an original 60gb Fat PS3 and 3g usb-device. Since wireless networks cost 3 legs and I only have two I was wondering if you guys/girls could help me figure out how to connect my PS3 to the 3g network. I have the cable required to connect my laptop to the PS3 but it would be great to get all sorts of noob proof 'How To' on how to do this. I have googled and googled and haven't found a good 'How To' to guide me through this. 

I know there are at least two ways to do this;
1. Connect directly using crossover cable
2. Create a router within the laptop to connect the PS3 wirelessly.

Please correct me if I'm wrong and have a good day :)

I am btw not a 100% sure this thread is in the right place so please forgive me, This forum is much different then those I have frequented.

---

### Post by collisionystm on 2011-12-01
>                                   **3g to PS3?**             
                                                                Hey people,

I have Ubuntu 04.11 or something like that in my Asus Eee-7000 laptop,  an original 60gb Fat PS3 and 3g usb-device. Since wireless networks cost  3 legs and I only have two I was wondering if you guys/girls could help  me figure out how to connect my PS3 to the 3g network. I have the cable  required to connect my laptop to the PS3 but it would be great to get  all sorts of noob proof 'How To' on how to do this. I have googled and  googled and haven't found a good 'How To' to guide me through this. 

I know there are at least two ways to do this;
1. Connect directly using crossover cable
2. Create a router within the laptop to connect the PS3 wirelessly.

Please correct me if I'm wrong and have a good day :smile:

I am btw not a 100% sure this thread is in the right place so please  forgive me, This forum is much different then those I have frequented.
You want to use the cable and turn your laptop into an internet router. Make sure your firewall is at defaults before doing this

Open terminal

sudo bash

paste

> iptables -F iptables -X iptables -t nat -F iptables -t nat -X iptables -t mangle -F iptables -t mangle -X iptables -P INPUT ACCEPT iptables -P FORWARD ACCEPT iptables -P OUTPUT ACCEPT/QUOTE]Shouldn't be to bad.

First thing you want to do is figure out what interface your 3G card is on your laptop.

Open a terminal

```
type ifconfig
```I assume you should see eth0, wlan0 (or eth1) and PPP0, so lets just go with that. 
The PPP0 should be your 3G

You will want to give your computer a static IP address on the nic port eth0

make it

[QUOTE]192.168.1.10
255.255.255.0Give your PS3 and IP address of

> 192.168.1.11
255.255.255.0
gateway 192.168.1.10
dns 8.8.8.8 << --- Google dns servers, they will work fine
back to terminal

```
sudo bash
``````
nano /etc/sysctl.conf
```un-comment (remove # ) from this line

```
net/ipv4/ip_forward=1
```save the file
now reset your networking

```
sudo /etc/init.d/networking restart
```now we will enable masquerade in your iptables to allow your ps3 to reach the net
```

sudo bash
``````
iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE
```you should be good to go

---

### Post by joi_gudni on 2011-12-01
wow, isn't this something, Thanks :)

but when ever i copy paste that first part i get;
> 
iptables v1.4.10: Cannot use -N with -F

Try `iptables -h' or 'iptables --help' for more information.

---

### Post by collisionystm on 2011-12-01
sorry the forums screwed it up lol.

You can probably skip it. I am sure your iptables are normal anyways.


so skip this mess


> [QUOTE]iptables -F iptables -X iptables -t nat -F iptables -t nat -X  iptables -t mangle -F iptables -t mangle -X iptables -P INPUT ACCEPT  iptables -P FORWARD ACCEPT iptables -P OUTPUT ACCEPT/QUOTE]Shouldn't be  to bad.

---

### Post by joi_gudni on 2011-12-01
I cant get past the ipconfig thing.. how do i change the addresses? 

You have to excuse me, i change into a retard when it comes to Ubuntu settings and Terminal and all.

---

### Post by collisionystm on 2011-12-01
> **joi_gudni said:**
> I cant get past the ipconfig thing.. how do i change the addresses? 

You have to excuse me, i change into a retard when it comes to Ubuntu settings and Terminal and all.


lol its cool.

there are 2 ways to do it.

one is through the Network Settings program on Ubuntu. Look for it in the menu's.

The other is through the terminal. They are both easy to do. 

Let me know what you want help with

---

### Post by joi_gudni on 2011-12-01
okay, i did all that although i skipped the first thing like you said and couldnt find out how to save this thing; 


nano /etc/sysctl.conf

I can now connect my laptop to the ps3 but the Ps3 cant connect to the network.. :/

---

### Post by collisionystm on 2011-12-02
nano /etc/sysctl.conf

un comment that line, like i said

press

CTRL + X then Y to save the file

restart networking

sudo service networking restart

or

sudo /etc/init.d/networking restart

make sure you do this part

sudo iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE

---

### Post by collisionystm on 2011-12-02
in the sysctl.conf file

this line 
net/ipv4/ip_forward=1

is what allows routing to happen. without this, your PS3 will never see the internet lol

---

### Post by joi_gudni on 2011-12-02
okay okay, after the change in the 'nano /etc/sysctl.conf' file i push ctrl-x and then y but now it says;

 'File name to write /etc/sysctl.conf'

and below that are all these guys;

ctrl-g get help, ctrl c cancel, M-D Dos Format, M-M Mac Format, M-A Append, M-P Prepend, M-B Backup file.

What do i do now?

---

### Post by collisionystm on 2011-12-02
> **joi_gudni said:**
> okay okay, after the change in the 'nano /etc/sysctl.conf' file i push ctrl-x and then y but now it says;

 'File name to write /etc/sysctl.conf'

and below that are all these guys;

ctrl-g get help, ctrl c cancel, M-D Dos Format, M-M Mac Format, M-A Append, M-P Prepend, M-B Backup file.

What do i do now?

just hit enter

---

### Post by collisionystm on 2011-12-02
restart networking when you are done with that

---

### Post by joi_gudni on 2011-12-02
Okay, now i establish Ip address but i dont get a connection..

While in the Ps3, what do i put in as Default Router?

---

### Post by collisionystm on 2011-12-02
> **joi_gudni said:**
> Okay, now i establish Ip address but i dont get a connection..

While in the Ps3, what do i put in as Default Router?

the laptop's ip address

192.168. blah blah

whatever you made the ethernet port

---

### Post by joi_gudni on 2011-12-02
i just found out i forgot to change the ip and all that crap on the laptop..

do i put the ip under DNS, search domains or something else?

---

### Post by collisionystm on 2011-12-02
> **joi_gudni said:**
> i just found out i forgot to change the ip and all that crap on the laptop..

do i put the ip under DNS, search domains or something else?


the only thing you want to do is put an ip address and subnet

so if you use a 192.168.1.XXX address, your subnet is 255.255.255.0

you dont need to add dns or domain

---

### Post by joi_gudni on 2011-12-02
**** this ****... im done for the day, ill maybe return tomorrow, thanks for the help anyway :)

---

