---
title: "not even able to ping other computers in LAN :'-("
date: 2012-03-22
forum: Networking &amp; Wireless
---

### Post by utkarsh009 on 2012-03-22
Hi guys! I have a netbook with XP sp3 and Ubuntu 10.04 dual boot. I also have a desktop with Ubuntu 11.10. I have a crossover LAN cable and I want to connect both the computers for playing multiplayer games. I tried every possible way but failed. I was not even able to ping even after entering the IP address and subnet. I used IP address of the form 192.168.0.x where x is 1,2 and subnet 255.255.255.0. Both the computers were able to connect (network manager connected successfully) but I was not able to ping other computer's IP. (Ping only worked when I entered the same computer's IP :lol:) please help me connect both the computers using crossover Ethernet cable.

---

### Post by Insomn1a on 2012-03-22
> **utkarsh009 said:**
> Hi guys! I have a netbook with XP sp3 and Ubuntu 10.04 dual boot. I also have a desktop with Ubuntu 11.10. I have a crossover LAN cable and I want to connect both the computers for playing multiplayer games. I tried every possible way but failed. I was not even able to ping even after entering the IP address and subnet. I used IP address of the form 192.168.0.x where x is 1,2 and subnet 255.255.255.0. Both the computers were able to connect (network manager connected successfully) but I was not able to ping other computer's IP. (Ping only worked when I entered the same computer's IP :lol:) please help me connect both the computers using crossover Ethernet cable.


I dont really use crossover cables that much for PC's to communicate but take a look at this.

[http://answers.yahoo.com/question/index?qid=20090709083056AA0RqWV](http://answers.yahoo.com/question/index?qid=20090709083056AA0RqWV)

I know its an older version of ubuntu but maybe that can be of some assistance.

---

### Post by utkarsh009 on 2012-03-22
After trying so many things I decided to fall back to the basic settings and it worked.
only 2 problems remain : 
1. Whenever I copy the files from one PC to the other, the speed is 4.8Mbps but connection information shows speed of 100Mbps. Why?
2. I can't access files located on Ubuntu via XP. But I can do vice versa. (I have shared many folders on both PC.) Whenever I try to open Ubuntu computer from XP it shows I don't have permission although I am the administrator and that parameter is incorrect.
Please help!!!!

---

### Post by jonobr on 2012-03-22
Hello


I would recommend you close this thread and open two new ones,.

While your doing that though, 

Could you double check your bits and bytes?  
If the rate is 4.8MBps that would be 38.4 mbps which would sound right
If thats not it, then I would check the settings of your port ensuring they are not set to 10mpbs or that they are not half duplex or something like that. This can be found in ifconfig,
For your sharing, are you running samba?
If so give details on that.
Recommend hover, you open a new post for each as the X'd ethernet thing looks done here,.

---

### Post by utkarsh009 on 2012-03-22
Ok jonobr I'll be starting 2 new threads!!

---

