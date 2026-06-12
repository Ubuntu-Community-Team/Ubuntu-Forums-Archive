---
title: "Problem connecting to wireless home network"
date: 2009-01-24
forum: Networking &amp; Wireless
---

### Post by Decani on 2009-01-24
I am getting stressed out trying to connect to the internet on my PC. I installed Ubuntu 2 days ago and the program seems very good, but I am having problems connecting to my home wireless network. The network is being shown by Ubuntu as one of the networks in range and I have tried to connect without success several times. I have tried to edit the settings, but I am not sure what details should be entered. I have a Belkin router and the network is working okay on Windows on the same PC.

I receive a message after the connection times out stating that "Authentication required by wireless network", it also shows "Wireless Security as WPA & WPA2 Personal" and then the password. This won't connect and I am wondering how I can connect? Is there anyway that I can go to Windows and get the correct details from there? 

It's getting frustrating now.

Many thanks.:(

---

### Post by mikewhatever on 2009-01-24
It seems that the problem is that you don't know the password. Unfortunately, that's something you must know, and no, you can't get it from Windows while running Ubuntu.

---

### Post by Decani on 2009-01-24
I am fully aware that I cannot use Windows and Linux at the same time on the same PC. Perhaps I didn't make myself clear. I am trying to see if it is possible to obtain the network settings from my Windows PC first of all and then add the details to Ubuntu afterwards. 

I do have a log-in password for my home network and I have tried entering that in Ubuntu without success (I haven't forgotten it). Perhaps, I am entering the password in the wrong place?

Does anyone have any ideas please?

Thanks from a man who is fully aware that Linux is not Windows !

---

### Post by mikewhatever on 2009-01-24
Perhaps I don't quite understand your request, apologies for that, but what hinders you form booting Windows and getting whatever details and settings you need?

---

### Post by Decani on 2009-01-24
This is the information obtained from the my PC while using Windows. I am not sure who I should configure Linux with the details shown below. Are you able to help please?

Address type: DHCP

IP Address: 192.168.1.101

Subnet Mask: 255.255.255.0

Default Gateway: 192.168.1.1

Physical Address: 00-11-09-AF-5F4D

DHCP server: 192.168.1.1

DNS Servers: 194.168.4.100 and 194.168.8.100

Network Authentication: WPA-PSK

Data Encryption: TKIP

---

### Post by mikewhatever on 2009-01-24
Assuming you are on 8.10, which is a good default assumption, try clicking on the network manager icon, select 'Create New Wireless Network', and enter the required info. There is nothing special about the Windows settings you posted, so given the authentication is successful, it should connect. I can only add that wpa2 encryption has been working for me out of the box since Feisty, and I really don't know why it wouldn't connect when the correct password is entered.

---

### Post by Stunts on 2009-01-24
Hello!
I also have a Belkin router and it has some problems when I try to connect my linux pc to it. I think it has to do with the way DHCP works on both systems.
What I used to do when that started to happen is simply restart the router. In order to do that just unplug it from the AC power for like 10 seconds.
After that just connect normally. I used to have to do that like weekely, but after updating my router's firmware my resets went down to almost monthly schedule.

Belkin routers in my experience are great access points, but not so good routers...
I hope this info helps you out.

---

