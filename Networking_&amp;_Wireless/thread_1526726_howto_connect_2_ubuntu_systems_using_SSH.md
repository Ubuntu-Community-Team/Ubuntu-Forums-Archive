---
title: "howto connect 2 ubuntu systems using SSH"
date: 2010-07-08
forum: Networking &amp; Wireless
---

### Post by 987a654 on 2010-07-08
I am trying to connect two ubuntu 10.04 systems using ssh. Installed openssh-server on the server machine. Nmap says port 22 is open and assigned to ssh and 5900 open and assigned to vnc. 

server - ufw status -> inactive
client - ufw status -> active

I am using the following command on the client machine.

 ssh -C 202.xxx.xx.xxx -L 5900:10.xxx.xx.xxx:5900 -l pat

 202.xxx.xx.xxx is the external ip for the server, got it from whatismyip.com

10.xxx.xx.xxx is the internal ip for ppp0, got it from ifconfig.

Both the systems use huawei usb 3G modems. 

On the server I can connect to the localhost fine. So I am guessing, the server demon is running. 

I get these following errors listed @ /var/log/auth.log on the server

error: bind to port 22 on 0.0.0.0 failed: Address already in use
fatal cannot bind any addresses.

I tried using no-ip and installed noip2 from synaptic and now I cannot open it using sudo /usr/local/bin/noip2

it says can't locate configuration file /usr/local/etc//no-ip2.comf (try -c) ending

I just want to know how to get the noip2 gui back.

thank you 
Yudi

---

### Post by 987a654 on 2010-07-08
just an update

i used a different ISP which uses static ip and I could ssh with the following command

ssh -C 202.xxx.xx.xxx -L 5900:localhost:5900 -l pat

now both whatismyip.com and ifconfig give the same ip address.

I would still like to know how to connect to a 3g modem that uses dynamic IP addressing.

If it helps I am from Australia and three (ISP) uses dynamic ip address and Exetel (ISP) uses static IP. Anyone who successfully connected to a system using three Mobile Broadband service could offer insights, that will be great.

---

### Post by Cnothing on 2010-07-08
sorry i know im not on the right thread (idk how to start one) but anyways i was just wondering if there was anyone bored enough to help me out i know a good bit about 
computers but i want to keep learning more about anything and everything to do with them like networking , programming,tcp/ip protocols,..ect i mean i already know a good bit abut that stuff but would love to learn more

---

