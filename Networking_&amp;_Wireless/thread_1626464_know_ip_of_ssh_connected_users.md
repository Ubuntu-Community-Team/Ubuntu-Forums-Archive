---
title: "know ip of ssh connected users"
date: 2010-11-20
forum: Networking &amp; Wireless
---

### Post by merdaalcanto on 2010-11-20
Hello,

is there any log file where I can get the public ip address from a user who has tried to put a file into my computer by scp?


Let me explain the hole environment mess and see if maybe for my problem is another better solution.

I'm abroad and I connect to my home computer by ssh to a certain domain. My home's computer has dynamic IP address, so I have the routine which checks its IP address and automatically updates the DNS server. The thing is that once connected to my home computer I needed to connect throug a vpn to another network to be able to use svn. And until here everything is perfect. 

But... WTF!!!!  I have no more connection to my home pc!!! I checked the domain name and now it's pointing to the vpn network!!! ](*,) So I guess that my home pc has checked its public IP address while I was connected to the vpn and have updated the DNS. My hope is that somehow figure out which was the last IP address at which the domain name was pointing and try to connect to my home computer to teardown the vpn connection, or reboot the machine. I tried to upload a file with scp so if there is any log with ip addresses that would be nice. :)



Well thanks in advance.

---

