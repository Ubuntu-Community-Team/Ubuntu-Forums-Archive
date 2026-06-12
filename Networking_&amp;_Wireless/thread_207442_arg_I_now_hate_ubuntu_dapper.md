---
title: "arg I now hate ubuntu dapper"
date: 2006-07-01
forum: Networking &amp; Wireless
---

### Post by mrweirdo on 2006-07-01
I'm realy beging to hate ubuntu dapper as for the 4th time In a row my networking has completly stoped working entirely. Specificaly I am runing the server version. It seems to be useless if u have more then 1 nic. I have 3 one intel pro 10/100 going to my cable modem, one  intel pro 10/100 for internal wired lan, and finaly a d-link wda-2320 setup as a wap for the wireless network. 

Now neather the wired or wireless can access anything on the net via ip or dns. However they can still ping the linux box itself. I have no idea what went wrong as I had the server setup in a locked room with it setup in such a way no one but myself have access to the box other then to use it for nat purposes and it was chuging along perfectly for about three weeks. 

Ive tried just about everything to coax it back to life including  scraping all my network card setings in /etc/network/interfaces and them reseting them all up. Completly flushing out my iptables firewall and a rewrite of the entire script from scratch. Nothing seems to have worked just like all those other times my network has gone to hell. It seems to only thing that fixes it is a complete reinstall of the os but who wants to have to reinstall every couple of days to every few weeks? heck thats worse then windows lol.

I've now swaped my dell poweredge server out for an old desktop machine wich still has ipcop on it so I was able to get at least the wired lan back up for now. I'll probably give ubuntu anouther try by runing the full gui for awhile and seeing how that goes but I'm not gona be able to do any work on it untill next week as I'm leaving first thing tomorrow morning for vacation and I have to go pack so dont have time to mess with it now.

Ok that was my rant for the day :P

Anyone else notice some real flakelyness with ubuntu? or have any sugestions what might be causing my problem besides iptables since it doesnt seem to be releated to that?

---

### Post by thunderduck3141 on 2006-07-01
its not ubuntu
i am running my ubuntu with 5 connections, no prob

---

### Post by FujiMan on 2006-07-02
MrWeirdo,

I'm having problems too. I've installed the desktop OS wired directly to the switch and router, got all the updates. But when I moved the box to the basement (where I have a wireless bridge) the network setting just fails even whether I've set them to DHCP or a static ip. Route table comes up blank. I cant ping any machine in the basement lan. It is like the machine went stupid. I couldn't find a networking app to repair or re-configure the network. Maybe there is a utility to configure network cards that I dont know about.

FujiMan

---

### Post by mips on 2006-07-02
Try disabling IPv6.

---

### Post by mrweirdo on 2006-07-10
Just reinstalled last night and so far so good now even after multiple reboots it still seems to be working. Lets hope it remains that way now. One thing i didnt do before I noticed is setup gateways for the two internal lans both the wired and wireless before. Mayby that was part of the problem. I know have their gateways pointed to the same dedicated ips assigned to those two cards

---

