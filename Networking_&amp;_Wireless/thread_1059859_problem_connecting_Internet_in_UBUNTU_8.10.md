---
title: "problem connecting Internet in UBUNTU 8.10"
date: 2009-02-04
forum: Networking &amp; Wireless
---

### Post by shanto_eee on 2009-02-04
I am a nobish linux user.
facing problem with connecting internet in UBUNTU

Its a LAN connection but username and password protected. I had to setup IP and set username and password to dial the connection in windows XP.

In ubuntu I successfully configured IP and it can detect the connection but i cant configure the username and password[i tried to configure 802.1x config but when i try connection is disconnected]

-----------------------
In XP I followed the following procedure:

1. Contrl Panel -> Network connections -> Creat a new connection 

2. from connection wizard---connect to the internet->setup my connection manually->connect using a broadband connection which uses a username and password->

3. then complete the procedure

4. then i have to confifig the IP
--------------------------
plz let me solve the problem

SHANTO

---

### Post by Fire_Chief on 2009-02-04
It sounds like you have a PPPoE DSL connection. You could try configuring a DSL connection from NetworkManager.

Go to System -> Preferences -> Network Configuration
Click on the DSL tab in the window.
Click Add
Give it a name for the connection
Fill in your username and password (don't worry about the service field).
Click Ok
Close the Network Connections box
Left click on the NetworkManager applet in the panel and see if your new connection is listed. If so, click on it and see if it connects properly.

Cheers!

---

### Post by shanto_eee on 2009-02-04
Thnx
let me try it

:D

---

