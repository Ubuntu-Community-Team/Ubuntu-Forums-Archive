---
title: "network configuration in 9.04"
date: 2009-10-02
forum: Networking &amp; Wireless
---

### Post by shashikant876 on 2009-10-02
Dear All

I have been using Ubuntu since version 6.10

Till version 8.04 i am using LTSP with a thin client setup

Network configuration is easy i just have to put ip address subnet mask and gateway

For lancard which uses to connect to mailserver and internet proxy server

172.16.97.55
255.255.255.0
and gatway is 172.16.97.54

and for the lancard which is used to connect other thin clients i have to just put ip address and subnet mask

192.168.0.1 
255.255.255.0

and then i run sudo sudo ltsp-update-sshkeys and sudo ltsp-update-image

and the thin clients are able to boot

but this interface changed in 9.04

there are 5 tabs ie wired wireless mobile broadband vpn and dsl

i am able to give ip address in wired and then go to edit and put ip address 

but it does not boot my thin clients 

as a way around i simply took a copy of my etc/network/network interface file in 8.04  to 9.04 and i am able to boot thin clients and the setup works fine

but even in 9.10 the same system is there. so is there a simple way to do this just like in 8.04 bcoz i am not a geek in command line and text file interfaces.

i have a windows gui mentallity 

please help me with this  

Thanx in Advance

Regards
Shashikant

---

