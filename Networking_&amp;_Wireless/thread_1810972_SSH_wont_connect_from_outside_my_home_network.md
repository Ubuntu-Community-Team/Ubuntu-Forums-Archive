---
title: "SSH wont connect from outside my home network"
date: 2011-07-24
forum: Networking &amp; Wireless
---

### Post by Tsquad on 2011-07-24
I just got done setting up an SSH SFTP server on a clean install of ubuntu 9.10. I can connect to the SSH terminal and the SFTP server via putty and filezilla respectively. When i try and access either of them by typing my external ip address i get:

Error:	Connection timed out
Error:	Could not connect to server

I do have internal static Ip address's on all my computers, and i do have port 22 forwarded to the correct static IP. 

Does anyone have any clue as to my issue with external connection. 

My router is a DLink DIR-628 if that helps.

---

### Post by 2F4U on 2011-07-24
Do you have a firewall in the router that may prevent access?

---

### Post by papibe on 2011-07-24
By any chance are you trying to connect using your external IP, but from inside your network?  That usually does not work due to restrictions on most routers.

In order to test ssh access from outside your network, you have to do it from outside: a Internet Cafe, a Public Library or better a friend house.

Also you have to forward the port 22 in your router to the LAN IP of the machine you want to connect.

Hope it helps.
Regards

---

### Post by Tsquad on 2011-07-24
Ok, I solved the problem by messing around with my router more. Not exactly sure what i did that fixed it as i did a few things at once. But i can now test it using my external ip and connect just fine. 

Problem solved, but thanks guys.

---

### Post by brickedone on 2011-08-29
facing very similar issue, would really love to find out how you solved it

---

