---
title: "Local network but no internet"
date: 2009-05-09
forum: Networking &amp; Wireless
---

### Post by defort on 2009-05-09
I am clearly a newbie.  I had Ubuntu installed on my computer by a student at the university.  Wired and wireless connections work at the university. When I bring the computer home I can not get the internet on my wired or wireless system (all other computers are working).  On the wired network at home I can see and access the other computers using the Ubuntu computer so I know the hardware is not the issue.  It may be that the sign-in I use at the university has been set as a default and it does not work for the home network (different sign-in).  Of course I have no real idea and do not know where to find or change the settings. Can anybody advise or recommend a solution?

---

### Post by Iowan on 2009-05-09
If you can see/access local machines, but cannot get to internet, it's possible that the gateway address is wrong. *Usually*, DHCP server tells machine where to look. Does your machine use DHCP?

---

### Post by abn91c on 2009-05-09
right click on your network connection icon>edit connections>wireless tab
then enter your networks SSID and wireless security key, make sure you save the settings and the "connect automatically" Box is checked

---

### Post by defort on 2009-05-10
> **abn91c said:**
> right click on your network connection icon>edit connections>wireless tab
then enter your networks SSID and wireless security key, make sure you save the settings and the "connect automatically" Box is checked


Mode:  Should this be Infrastructure or Ad-hoc

---

### Post by defort on 2009-05-10
> **Iowan said:**
> If you can see/access local machines, but cannot get to internet, it's possible that the gateway address is wrong. *Usually*, DHCP server tells machine where to look. Does your machine use DHCP?

Yes DHCP is used.  For the Wired connection interface: Ethernet (eth0) the IP Address shown in the Active Network Connections is the IP Address of the Barricade Broadband Router.  Other Windows computers wired to the router work.

Is there something in Ubuntu I must do?

---

### Post by abn91c on 2009-05-10
infrastructure mode

---

