---
title: "allow nonnetworked computers to connect to my ssh server"
date: 2010-02-26
forum: Networking &amp; Wireless
---

### Post by WinterMadness on 2010-02-26
i have ssh running, and i can connect to it from my other computer just fine, but when i  try to connect to it from a computer outside my network it does not work. i have port forwarded port 22 to the machine running the server, what else do i need to do?

edit: i get the error no route to host

---

### Post by iponeverything on 2010-02-26
your a bit short on details.

Are you ssh'ing to private address from a public address when you should be ssh'ing to the public address of the machine doing the port forwarding? Does the thing doing the port forwarding indeed have a public address?

---

### Post by WinterMadness on 2010-02-26
> **iponeverything said:**
> your a bit short on details.

Are you ssh'ing to private address from a public address when you should be ssh'ing to the public address of the machine doing the port forwarding? Does the thing doing the port forwarding indeed have a public address?

well Ill tell you what i do know.

my local ip for the machine running the SSH server is 192.168.1.39 when I type ssh 192.168.1.39 it takes about two seconds and itll  ask me for a password and ill have root access to my other machine.

However, when I try to access it using the IP I get from whatismyip.com it will say no route to host. 

I have port forwarded port  22 (from my router) to the machine running the server 

I turned off my routers firewall

I turned off UFW. When I port scan I dont see port 22 open....

I dont know that much about this stuff so excessive details are very welcome :) Unfortunately this is all I know, and if you can ask me to do specific things to get info I can do that.

---

### Post by Andreasvo on 2010-02-26
Is the router you are forwarding port 22 in the only network device you have? Or do you for example have a DSL modem? 

If you have a network device before the router you also have to forward port 22 from that device to your router.

---

### Post by WinterMadness on 2010-02-26
i have a dsl modem with a router built in it. its all one box

---

### Post by WinterMadness on 2010-02-26
anyone?

Now I have it at the point where when I try to connect to the IP I get from whatismyip.com I can log into it.

However, thats only if im on the  network. Im on another network and the server is definitely running. I cant get it to connect though

---

### Post by Mike'sHardLinux on 2010-02-26
What's the make and model of your DSL modem?

---

### Post by WinterMadness on 2010-02-26
> **Mike'sHardLinux said:**
> What's the make and model of your DSL modem?

Westell 7500 I believe. It comes with Verizon.

---

### Post by efflandt on 2010-02-26
Many routers or modem/routers do not do loopback (LAN2LAN via WAN IP) and neither does Linux when it is acting as a masquerading router.  For security reasons it does not trust a LAN IP coming in its public interface  (IP spoofing).

So you may need to test the internet connection using dial up networking from a machine not on your LAN, a mobile data network, or some host on the internet (ssh to a free shell account, and from there ssh back in).

---

### Post by Mike'sHardLinux on 2010-02-26
> **WinterMadness said:**
> Westell 7500 I believe. It comes with Verizon.

I just want to clarify. You did say you CAN ssh via the Public IP when you ssh from your LAN, but you CANNOT from outside of LAN, correct? Where is the "other" network you are referring to? Can you elaborate some more?

Are you sure you have your port forwarding properly configured? I noticed there is a setting in there for Host or Dynamic. You should have it set to Host for what you are wanting. 

It is entirely possible you have made a typo or some other error somewhere. I assume you have double-checked  all your settings, etc...

---

### Post by WinterMadness on 2010-02-26
> **Mike'sHardLinux said:**
> I just want to clarify. You did say you CAN ssh via the Public IP when you ssh from your LAN, but you CANNOT from outside of LAN, correct? Where is the "other" network you are referring to? Can you elaborate some more?

Are you sure you have your port forwarding properly configured? I noticed there is a setting in there for Host or Dynamic. You should have it set to Host for what you are wanting. 

It is entirely possible you have made a typo or some other error somewhere. I assume you have double-checked  all your settings, etc...

Indeed, you have it right. I can ssh my public ip (when I goto whatismyip.com this is the IP i refer to as my public one)from my lan, but when I try to ssh that same ip from another network (im at  now) it just times out.

This other network is the public wifi at my job. I dont know the settings here, but I doubt they have outbound requests blocked? 

I have set it to host.

---

### Post by WinterMadness on 2010-02-26
bizump

---

### Post by WinterMadness on 2010-02-27
now im nmapping the IP at my house: heres what it says


Interesting ports on myip:
Not shown: 994 closed ports
PORT     STATE    SERVICE
22/tcp   filtered ssh

Shouldnt it be "open"? like the other ports are?

how do I change this?

---

### Post by WinterMadness on 2010-02-27
Oh I also forgot to mention in my last post that when I try to connect I get timed out. Im wondering if its because its filtered

---

### Post by WinterMadness on 2010-02-27
a few more bumps are in order

---

### Post by gordintoronto on 2010-02-28
Have you gone through this guide?
[http://linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch07s03.html](http://linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch07s03.html)

---

### Post by WinterMadness on 2010-02-28
unfortunately that guide doesnt seem to go anywhere  near my problem.

I really just need to know why my port is filtered and some kind of direction on how to change that.

---

