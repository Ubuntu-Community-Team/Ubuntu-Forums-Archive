---
title: "Ethernet Problem: Can't See Anything!"
date: 2009-04-25
forum: Networking &amp; Wireless
---

### Post by nickwalnut on 2009-04-25
Hello, I've just installed the newest version of Ubuntu (first time user) and have not had any luck at all connecting it to my network.
 
I have a Windows XP gateway connected to an Optus modem, and a central switch to which the other 4 Windows PC's in the house connect to. They can connect to the internet through the Win XP PC easily. My ubuntu PC however cannot even see the network, let alone connect to the internet.
 
I've set the network settings to the same as I would set my other computers on the network (with a different IP ofcourse) but am not getting any results. When I go to Network all I see is a "Windows Network" icon which responds with "Unable to mount location: Failed to retreive share list from server". I cannot ping anything, and despite changing network settings over and over again to experiment I have gotten nowhere.
 
Have I missed a crucial step, or is something wrong with my setup?
Thanks in advance.

---

### Post by wsbones on 2009-04-25
I'm a newbie but I had this error and fixed it by adding a rule under preferences/policy in firestarter to allow  192.168.2.0/255.

I had my network working fine under Ububtu 8.10 but upgrading to 9.04 produced the error.

---

### Post by nickwalnut on 2009-04-25
Is firestarter already installed in the Ubuntu distro? If it's not, then I don't have it (I haven't installed anything yet).

---

### Post by wsbones on 2009-04-26
I had firestarter installed under 8.10 and it seems to have carried over in the update.  

Yesterday I had my network operating correctly but today after shutdown and startup, I can see the other machines but get the "unable to mount" error.  

I disabled the firewall and now I can mount the other machines.

Bill

---

### Post by Iowan on 2009-04-26
From the sound of it, you are using static addresses? Can the Ubuntu machine **ping** other machines? Also, you might open a terminal and check **ifconfig -a** to verify that your machine got an IP address.

---

### Post by nickwalnut on 2009-04-27
I am using static IP addresses (just like all the other PCs on my network). ifconfig reports that the IP address has been assigned to eth0.
 
I can't ping any machines on the network currently, but I'm converting another old box to Ubuntu to see if I can ping *it* then - I'll report back when I'm done.
 
**EDIT:** I have installed Ubuntu on another machine, and they now can both ping each other, but ONLY each other. Any ideas as to why they can't see my Windows machines?

---

### Post by Iowan on 2009-04-27
Are you (or have you tried) pinging by IP address?

---

### Post by nickwalnut on 2009-04-29
OK, I seem to haved fixed the problem (it was a hardware issue).
 
Thanks for your replies. :)

---

