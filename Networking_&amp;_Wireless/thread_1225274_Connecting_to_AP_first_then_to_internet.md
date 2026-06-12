---
title: "Connecting to AP first then to internet"
date: 2009-07-28
forum: Networking &amp; Wireless
---

### Post by Bene Elim on 2009-07-28
Hello everyone!

I've been away from linux for a loong time. I've just installed ubuntu 9.04 on my laptop. The problem is I'm having trouble connecting to the internet. In windows first I connect to my AP and then to internet (I had to make a connection in windows, enter username, password etc.) because my dsl modem refuses to do it automaticaly. Now, the question is how do I make that kind of connection in ubuntu??? I have no problems connection my AP, but when i tried making DSL or wired connection in network manager nothing happened.

Thx

---

### Post by Bene Elim on 2009-07-28
I managed :D Connected to my AP first, then used pppoeconf to make a new connection, thanks anyway ):P

---

### Post by rahulsingh.nitrkl on 2009-07-28
What is AP? I have problem configuring pppoe. Please let me know how you did it. Thanks

---

### Post by Bene Elim on 2009-07-28
AP = wireless acess point

I started terminal, entered sudo pppconfig and typed there my username and password...and everything from there on is automatic.

However, I have a new problem now, after I connected I updated everything and now it won't connect again :(
Seems a new kernel is installed Ubuntu 9.04, kernel 2.6.28-13 generic, and there's still 2.6.28-11, no matter which one I use I can't connect. Wireless manager says "Device not managed". Anyone know how to fix that?

---

### Post by superprash2003 on 2009-07-28
try this [http://www.prash-babu.com/2009/05/how-to-fix-ubuntu-network-manager-error.html](http://www.prash-babu.com/2009/05/how-to-fix-ubuntu-network-manager-error.html)

---

### Post by Bene Elim on 2009-07-28
thanks superprash2003, sudo gedit /etc/NetworkManager/nm-system-settings.conf worked, had to do sudo ifconfig wlan0 down then up, and now it's running again :D 

cheers

---

