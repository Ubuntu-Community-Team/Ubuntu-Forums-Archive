---
title: "External request only work for gateway but not for my static IP address"
date: 2009-01-07
forum: Networking &amp; Wireless
---

### Post by horowitzathome on 2009-01-07
Hello!

I have a very wired problem I try to explain. 

IT Configuration:
ADSL Modem with PPTP connection in bridge mode.
Router which does the login to the PPTP connection. 

Communication between modem and router:
ADSL port 10.0.0.138.
Router port 10.0.0.140.

Linux (UBUNTU 8.10) PC connected to the router. 

From my provider I got 5 static ip addresses and a gateway address. Lets call them X.X.X.113 (X113 for this description) to X.X.X.118. The X113 is the so called gateway. 

With the router I configured a DMZ with ip address X116 and this address I have assigned to my PC. The address of the router is X114.

For the modem and router I disabled the firewalls and on my PC runs the firewall FIRESTARTER. 

Connection to the internet works, i.e. router does the login via the modem. The ADSL connection is a so called dynamic ADSL connection. 

The addresses are then as follows:
Modem WAN: X113
Modem LAN: 10.0.0.138
Router to modem: 10.0.0.140
Router LAN: X114
PC LAN: X116

When I open a browser window and call an external web application to show my IP address it says X113. I guess this is because of the PPTP connection. This is the first thing where I am not sure if this is correct, I would have expected X116, but maybe this is okay. 

On my firewall I added the rule to accept connections (inbound) for port 30000 and any ip address. I wrote a little JAVA program to listen to port 30000 which runs on my PC.

Now the scenarios: 

When I run a client on my PC to connect to port 30000 this works -> OK.

When I make a port test with an external web application (i.e. the request comes from somewhere inbound to my PC) the situation is as follows: 

Address X113 and port 100 -> firewall blocks -> OK. Actually I am wondering why the request comes to my PC with address X116 but obviously all requests coming from the gateway (X113) are forwarded to X116 because this is the DMZ PC or because they come from the gateway. 

Address X113 and port 30000 –> firewall accepts and my test program gets the request -> OK (I guess). The web application says port open.

Address X116 and port 100 -> firewall blocks (I see it in the blocking window) -> OK. The web application says port closed.

Address X116 and port 30000 -> firewall does not block (nothing shown in blocking window) but the request is not reaching my test program -> This is not OK. The web application says port closed. 

So the final question is: why is a request for X113 and port 30000 accepted and reaching my test program respectively why is a request for X116 and port 30000 obviously accepted by my firewall (which I expected) but not forwarded to my test application? 

Does anyone have any idea? 

Best regards, Georg

---

