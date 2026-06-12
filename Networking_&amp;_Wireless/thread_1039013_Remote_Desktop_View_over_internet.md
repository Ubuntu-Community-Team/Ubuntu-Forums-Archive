---
title: "Remote Desktop View over internet"
date: 2009-01-14
forum: Networking &amp; Wireless
---

### Post by ahddm on 2009-01-14
Ok, I need some help I have a friend that just got into linux and I am helping he get basics and stuff but I can't be over 24/7 I was wondering how I can set up a remote view so I can show him basic stuff he doesn't get from my pc instead of going over or tring to explain in chat.

---

### Post by Montblanc_Kupo on 2009-01-14
Yes please! +1

---

### Post by Aleanthus on 2009-01-14
i heard that Teamviewer should work well with wine, but i didnt try it out yet. maybe it helps.

also theres tightvnc, but thats a bit more complicated to setup i think.

(yay, first post and alrdy helping)

---

### Post by superprash2003 on 2009-01-14
hope this helps [http://www.prash-babu.com/2008/06/how-to-remote-control-your-ubuntu.html](http://www.prash-babu.com/2008/06/how-to-remote-control-your-ubuntu.html)

---

### Post by ahddm on 2009-01-14
I checked out your link, my friend has it set up to allow connections, one thing I can't figure out is this step: 

Step 1:Go to the terminal(Applications->Accessories->Terminal) and type vncviewer myname.servehttp.com:0 where myname.servehttp.com is your free domain name

Do you have to have a domain name?

---

### Post by superprash2003 on 2009-01-15
well that domain name is free to get.. its not necessary its just easier as its easier to remember domain names than ip addresses .. especially if its a dynamic ip which changes frequently.. if not, you could just go to [www.whatismyip.com](www.whatismyip.com) and get that person's ip addres.. and then replace that ip with myname.servehttp.com to connect..

---

### Post by ahddm on 2009-01-18
Sorry took so long to get back to this, I keep getting
vncviewer: ConnectToTcpAddr: connect: Connection refused
Unable to connect to VNC server

---

### Post by superprash2003 on 2009-01-18
in that case , something is blocking it.. do you have firestarter or any other firewall installed?? post output of sudo iptables -L

---

