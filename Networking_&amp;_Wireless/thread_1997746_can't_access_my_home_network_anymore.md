---
title: "can't access my home network anymore"
date: 2012-06-05
forum: Networking &amp; Wireless
---

### Post by malapradej on 2012-06-05
Hi,
I have been at this for some time and been through many posts without luck, thus turning to the experts for help....
I have previously setup a home network as follows:
desktop - wireless (the server - kinda) ubuntu 12.10
laptop - wireless ubuntu 12.10
netbook - wireless ubuntu 11.10
all runnung through a virgin media supplied router.
Note that I have recently upgraded the desktop and laptop to 12.10.
The netbook can still access the desktop, but even though some traces of the working network exists (icons) I am not able to connect between the laptop and desktop.

In my nautilus bookmarks I click on the LAPTOP icon.
The error message on the desktop side trying to connect to laptop:
Could not display "smb://192.168.0.4/"         
Error: Failed to retrieve share list from server
Please select another viewer and try again

!!!!!!Note the correct address is 192.168.0.5, the one in the message!!!!!

If I try and connect from the laptop the error is:
Unable to mount location
HTTP Error: Cannot resolve proxy hostname ()

I have tried changing the order of host etc in smb.conf file etc. and this does not work.

Your help will be much appreciated.

Jacques

---

### Post by cariboo on 2012-06-07
Do the systems on your network have static or dynamic ip addresses? If dynamic they could have changed. To check, in a terminal type the following command:

```
sudo nmap -sP 192.168.0.0/24
```

In order for the above command to work, you have to have nmap installed, THe output should look similar to this:

> sudo nmap -sP 192.168.1.0/24
[sudo] password for cariboo: 

Starting Nmap 5.51.6 ( [http://nmap.org](http://nmap.org) ) at 2012-06-06 21:37 PDT
Nmap scan report for 192.168.1.1
Host is up (0.00063s latency).
MAC Address: 00:00:00:00:00:00 (Cisco-Linksys)
Nmap scan report for 192.168.1.2
Host is up (0.0024s latency).
MAC Address: 00:00:00:00:00:00 (SMC Networks)
Nmap scan report for 192.168.1.102
Host is up (0.00013s latency).
MAC Address: 00:00:00:00:00:00 (Elitegroup Computer System Co.)
Nmap scan report for 192.168.1.104
Host is up (0.00072s latency).
MAC Address: 00:00:00:00:00:00 (VD Division, Samsung Electronics Co.)
Nmap scan report for 192.168.1.225
Host is up.
Nmap scan report for 192.168.1.230
Host is up (0.00072s latency).
MAC Address: 00:00:00:00:00:00 (Brother Industries)
Nmap scan report for willy (192.168.1.250)
Host is up (0.00019s latency).
MAC Address: 00:00:00:00:00:00 (Micro-star Int'l Co.)
Nmap done: 256 IP addresses (7 hosts up) scanned in 1.96 seconds

**Note 1:** If the wireless devices don't show up in the listings, run the same command from a device that is connected via wireless.

**Note 2:** I changed the mac addresses to all zeros

---

