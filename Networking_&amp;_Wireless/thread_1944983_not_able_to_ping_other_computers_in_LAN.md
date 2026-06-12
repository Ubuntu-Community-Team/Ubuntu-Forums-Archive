---
title: "not able to ping other computers in LAN"
date: 2012-03-22
forum: Networking &amp; Wireless
---

### Post by utkarsh009 on 2012-03-22
Hi guys! I have a netbook with XP sp3 and Ubuntu 10.04 dual boot. I also have a desktop with Ubuntu 11.10. I have a crossover LAN cable and I want to connect both the computers for playing multiplayer games. I tried every possible way but failed. I was not even able to ping even after entering the IP address and subnet. I used IP address of the form 192.168.0.x where x is 1,2 and subnet 255.255.255.0. Both the computers were able to connect (network manager connected successfully) but I was not able to ping other computer's IP. (Ping only worked when I entered the same computer's IP :lol:) please help me connect both the computers using crossover Ethernet cable.

---

### Post by MagneticFlux on 2012-03-26
I can't help you with your problem; but your post is in the wrong category and relevant people most likely wouldn't find it here. Try "Networking & Wireless" here: [http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)

---

### Post by rmil on 2012-03-26
In the case with crossover cable there is no automatic DHCP which means that ip numbers for both computers has to be set up manually. For example on can be 192.168.1.222 other can be 192.168.1.223. Seems that you have figure out that.

Now the most important thing is to make one of them to share connection:

1) Graphically you can click on Network Manager and edit connection to make it sharable.

Other way 

2) Use terminal CTRL-ALT-T and make one of them route for example type:
```
sudo route add default gw 192.168.1.222 eth0
```
on computer with 192.168.1.223 if this is the one with Internet connection.

---

### Post by mörgæs on 2012-03-26
Thread moved.

---

