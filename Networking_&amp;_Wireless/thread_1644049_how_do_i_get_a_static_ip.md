---
title: "how do i get a static ip"
date: 2010-12-12
forum: Networking &amp; Wireless
---

### Post by philipballew on 2010-12-12
i want to get a server running with a static ip address and allow the server to be accessed then from outside my network by ssh. how can  acquire a static  address to do this?

---

### Post by wannabegeek on 2010-12-12
I did it my getting a free account at DnyDNS.com or similar.
They take your dynamic IP and query it for when it changes and update their DNS server...
DnyDNS allows one free static IP...

I use dd-wrt on my router which has a setting for this...there is also a software which will manage the 
updating...forgot what it is called.

I gave my server a static IP behind my router thru dd-wrt....

that was about it...I spent some time setting up ssh, you'll need ssh.d installed from repo on the server. I recall there being a config file in /etc/ssh  to which you add your username and password.

I don't remember the details too well, but that should help you get started...good luck
wbg

---

### Post by philipballew on 2010-12-12
is there any sort of guide on how to set up dynamic ip address and how do i set up dynamic as apposed to static? like in terms of typing what into the computer when it asks what my address is?

---

### Post by CiSC0kid on 2010-12-12
There are a lot of things that need to happen with this. I am not very experienced with using linux as a server, but to make a static IP address in Linux, you go to your network manager tool and select the connection you want to edit for ex. auto ath0, auto wlan0. Input the IP address you want to assign to that connection in the IPv4 section. If your behind a router you might want to disable DHCP, though if you set the range of IP addresses manually you can leave DHCP on. Example:
DHCP On
DHCP Starting IP address: 192.168.1.3
Server IP: 192.168.1.2
Gateway: 192.168.1.1

This makes it so no other device is assigned your server's IP.

There is a bunch of other stuff to worry about if you are behind a router. I hope this answers a few questions.

---

### Post by philipballew on 2010-12-12
i would immagine if since my server is located at a place with att dsl id have to pay for a static ip with my router and since i need to get to my server from behind the router i guess ill need to know how to do this.

---

