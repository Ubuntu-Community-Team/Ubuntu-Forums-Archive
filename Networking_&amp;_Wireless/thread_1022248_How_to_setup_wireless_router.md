---
title: "How to setup wireless router"
date: 2008-12-26
forum: Networking &amp; Wireless
---

### Post by luchalibre383 on 2008-12-26
I am trying to setup a wireless router without the help of the I.S.P. The Internet provider is road runner and they will only provide a static ip address and not the other parts of the information that I need to setup my router.
Is there away to type in a command form the command line to give me the ip information that my router needs to operate properly.
I waited almost thirty minutes for no help and do not want to call them again. 
My cable modem works fine and would just need the info for the setup.
It comes with a cd that works for windows to automatically gathers the information for the router.

I wish there was a program like this for Linux.

Thanks

---

### Post by lsutiger on 2008-12-26
You should be able to setup the router to get the IP address dynamically, then all of the information should be viewable somewhere on your router. Then you can enter that information to the router. Just make sure the IP address is the same as tehy gave you.

As far as roadrunner not giving you the rest of the info, that's just bas customer service.

PS - Are you paying them for a static IP?

---

### Post by melojo on 2008-12-26
> **luchalibre383 said:**
> I am trying to setup a wireless router without the help of the I.S.P. The Internet provider is road runner and they will only provide a static ip address and not the other parts of the information that I need to setup my router.
Is there away to type in a command form the command line to give me the ip information that my router needs to operate properly.
I waited almost thirty minutes for no help and do not want to call them again. 
My cable modem works fine and would just need the info for the setup.
It comes with a cd that works for windows to automatically gathers the information for the router.

I wish there was a program like this for Linux.

Thanks

What brand of router is it?
You should be able to access the router settings through a web browser without the need of the cd.
Linksys ip to access the router is usually 192.168.1.1 and belkin is 192.168.2.1.  I am sure others are similar.

---

### Post by Jakey_TheSnake on 2008-12-26
To expand on the above post, BT is a common router make and their default address is 192.168.1.254

---

### Post by luchalibre383 on 2008-12-26
I have no problem getting into th control screen of the router but with entering the numbers so that the router can conect to the internet.

i am not sure if it is static or dynamic? What is the difference between the two???

Will this command work in terminal    ifconfig

Once I have this info which numbers to input in the correct places

---

### Post by melojo on 2008-12-26
static ip is one that is permanent and dynamic is one that changes.

You should have a setting in your router to enter the static ip and then you want your pc to be setup for dhcp or to give it an ip.

---

### Post by lsutiger on 2008-12-26
I am not sure where you are located, but most ISPs dish out dynamic IPs, so you should setup the router for that. 

To get a static IP from ISP, there is usually an extra monthly charge. (At least here in the US)

PS - What is the brand and model of the router?

---

