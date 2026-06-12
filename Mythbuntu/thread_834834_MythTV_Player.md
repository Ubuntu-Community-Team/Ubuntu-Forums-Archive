---
title: "MythTV Player"
date: 2008-06-19
forum: Mythbuntu
---

### Post by dareofficer on 2008-06-19
Hello, I have installed MythTV now and it works just fine.  I even have my directTV working and recording.  I need help however on the "PC" player that I installed on my PC's to watch the backend server.  When I click on the MythTV Player Icon, it asks for the name of the server, when I enter it. "mythtvtest" I get a errorcode of 10061, saying mythtest port:6543 error from socket connect failed.  My front end works fine on my Linux box, can someone please help with this?

---

### Post by stevecartermo on 2008-06-20
I enter the IP address, instead of server name ... seems to work for me.

---

### Post by uopjohnson on 2008-06-20
Sounds like a name resultion problem like stececartermo said, however it could also be any number of network problems.  Can you ping the backend from the machien you are installing on:
ping mythtvtest in start->run

---

