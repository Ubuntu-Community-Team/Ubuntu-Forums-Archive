---
title: "setting up home workstations with Ubuntu"
date: 2010-02-21
forum: Networking &amp; Wireless
---

### Post by oldwindows geek on 2010-02-21
Here is my delema, I have 4 machines 2 running Ubuntu 9.10, and one running windowsXP, and the forth will be Windows XP, only because some of my printer functions I can only get to work with windows, previous to upgrading to Ubuntu 9.10, I had everything working fine, my windows could see my Ubuntu's and my Ubuntu could see my windows, at that tine only had 1 ubuntu, now windows cannot see ubuntu and ubuntu cannot see ubuntu, my plan is to switch to mythbuntu , when I get things working, because I plan on adding 3 more machines, I have Gadmin-Samba installed on my ubuntu machines, do I need anything else. after upgrading to ubuntu 9.10, I had a system crash and had to start all over, this is just a home network with only one user. help please

---

### Post by Iowan on 2010-02-21
The new Ubuntu machine gets an IP address (check with **ifconfig -a)?**

---

### Post by oldwindows geek on 2010-02-22
when I check the network connection it gives me an IP address of 192.168.1.100 broadcast address of 192.168.1.255 subnst  255.255.255.0 defult 192.168.1.1 primary dns, 142.165.200.5 secondarydns 142.165.21.5, this is the same for all other machines IP address is 192.168.1.101 and 102

---

### Post by Iowan on 2010-02-22
Samba has evolved away from me (I understood it a few years ago...). Check */etc/samba/smb.conf* to verify that machines are in same workgroup (there's probably an easier way...)

---

### Post by oldwindows geek on 2010-02-23
same config file just copied from machine to machine, to make things easy, still no progress.

---

### Post by idlemind324 on 2010-02-23
Can we get the IP addresses of all 3 or at least verify they are all on the same subnet and can reach other (ping tests?)?

Are the other settings like DNS / default gateway the same?

Is windows file and print sharing turned on for the XP client?

Samba installed on both Ubuntu installations?

Are any firewalls enabled on any of the OS's that may be blocking traffic?

Are the computers in the same workgroup?

Can the Ubuntu workstations share files via SMB/CIFS between each other and just not the XP client and vice versa?

Thanks,

---

### Post by oldwindows geek on 2010-02-25
Here's an update, now have 2 machines with windows Xp one desktop, 1 laptop, they can talk back and forth 2 linux Ubuntu 9.10, they can talk to the XP desktop and laptop, but not to each other.  IP for linux is 192.168.1.102 and 101, Broadcast address is 192.168.1.255 for both, Subnet Mask 255.255.255.0 for both,Default Route 192.168.1.1, Primary DNS 142.165.200.5 Secondary DNS 142.165.21.5, the last 3 appear the same for both Linux machines:confused:. all 4 machines have the workgroup set the same

---

### Post by oldwindows geek on 2010-03-02
no fire walls at this time on the Ubuntu machines, same workgroup, windows file and printer share on,Samba installed both Ubuntu machines, can transfer files from Ubuntu to windows no problem, cannot go from Ubuntu to Ubuntu, or windows to Ubuntu.
     Printer on windows machine can print from either, Ubuntu, no problem

---

