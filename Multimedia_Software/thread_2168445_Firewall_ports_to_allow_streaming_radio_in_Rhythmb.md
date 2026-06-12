---
title: "Firewall port/s to allow streaming radio in Rhythmbox player?"
date: 2013-08-17
forum: Multimedia Software
---

### Post by Michael_LaBash on 2013-08-17
I have just set up my firewall with some basic settings....but now I can't get my favorite streaming audio station in Rhythmbox. It just says (Paused) next to the station and never plays.If I disable the Firewall it plays just fine.  Does anyone know how to open up the firewall to listen to streaming radio?

This is the URL I am trying to listen to: 
[http://50.57.66.150:8000/jukejoint](http://50.57.66.150:8000/jukejoint)

Thanks!

---

### Post by GwL3eNC on 2013-08-18
Hi,

i cant find which port you need to open. One noob way to find out could be to
implement some logging rules.

iptables -A INPUT -j LOG --log-level debug --log-prefix "LOG_IN: " 
iptables -A OUTPUT -j LOG --log-level debug --log-prefix "LOG_OUT: " 
iptables -A FORWARD -j LOG --log-level debug --log-prefix "LOG_FOR: " 

Then you can examine the /var/log/syslog file to see which things are rejected.
You can do a

cat /var/log/syslog | grep LOG_OUT

for example. The logged things look similar to the rules you implenet with iptables.
Shure, it's normally not good, but you can clear the syslog file if it slain you. I'm not
shure, but i think

sudo /var/log/syslog >

can do this.

---

