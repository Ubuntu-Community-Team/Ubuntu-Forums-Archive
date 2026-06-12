---
title: "create pppoe client with servicename"
date: 2010-11-25
forum: Networking &amp; Wireless
---

### Post by skynoc on 2010-11-25
hello , 

i m new to ubuntu i want to create a pppoe client with a service name 
i used to create it with pppoeconf but it is not asking me for the service name 
i went to /etc/ppp/peers then i typed gedit dsl-provider

i opened the file 


# Minimalistic default options file for DSL/PPPoE connections
noipdefault
defaultroute
replacedefaultroute
hide-password
#lcp-echo-interval 30
#lcp-echo-failure 4
noauth
persist
#mtu 1492
#persist
#maxfail 0
#holdoff 20
plugin rp-pppoe.so
usepeerdns
nic-wlan0
user "fadib"



i put in the bottom servicename="ROG"

when i pon dsl-provider it said unrecognized option servicename 

i put in the header of the file this line :

pty "/usr/sbin/pppoe -I wlan0 -T 80 -m 1452 -S ROG"

nothing changed i still cant connect 

any idea will be helpful

---

### Post by dineshs on 2010-11-27
Use Network manager DSL tab
[http://ubuntuforums.org/showpost.php?p=9611450&postcount=2](http://ubuntuforums.org/showpost.php?p=9611450&postcount=2)

---

### Post by sagarthegreat1 on 2010-12-15
1. Install rp-pppoe [http://www.roaringpenguin.com/products/pppoe](http://www.roaringpenguin.com/products/pppoe)
2.After install,run pppoe-setup in terminal.it will ask some questions, answer them appropriately.
3.run sudo pppoe-start.if it connects, good enough.stop and enjoy.
4.otherwise open /etc/ppp/pppoe.conf
5. Find field ACNAME and attach your service name to it.
6.save and go to step 3

---

### Post by skynoc on 2011-01-15
hello 

the Kde Network Manager applet works only with wired connection , it doesnt work with wireless .
- winxp is very simple to change the service name for each pppoe you create ,why ubuntu is not ?

please help

---

### Post by na12 on 2011-01-18
Try this app,there is a servicename option

[http://gtk-apps.org/content/show.php/SetPPPoE?content=137542](http://gtk-apps.org/content/show.php/SetPPPoE?content=137542)

---

### Post by skynoc on 2011-01-21
thanks for the app but seems that the field service name is not working fine , because i have 3 different service names on the network and when i put the service name of the second pppoe-server it only connects to the first pppoe-server

---

### Post by skynoc on 2011-01-29
it was very easy in windows xp to add for each pppoe connection a different service name but in ubuntu it is so difficult to do it , turning around the earth 3 times is easier than creating a pppoe connection with different service name in ubuntu.

---

### Post by dineshs on 2011-01-29
I dont think service name has role in authentication. But If you want 3 seperate pppoe diallers(say with seperate username and password) try this
Run sudo pppoeconf,follow instructions and create a connection,rename it to say connection1
```
sudo mv /etc/ppp/peers/dsl-provider /etc/ppp/peers/connection1
```
Run sudo pppoeconf again and create another connection .rename it 
```
sudo mv /etc/ppp/peers/dsl-provider /etc/ppp/peers/connection2
```
repeat the procedure and create connection3
Now to connect the first one use ```
sudo pon connection1
```and to disconnect use```
sudo poff connection1
```similarly to connect second one use ```
sudo pon connection2
```and so on...

---

### Post by skynoc on 2011-01-31
well i tried this before and even i tried to put servicename="ROG" in the dsl-provider file but didnt work

# Minimalistic default options file for DSL/PPPoE connections

noipdefault
defaultroute
replacedefaultroute
hide-password
#lcp-echo-interval 30
#lcp-echo-failure 4
noauth
persist
#mtu 1492
#persist
#maxfail 0
#holdoff 20
plugin rp-pppoe.so
nic-wlan0
usepeerdns
nic-wlan0
user "ism1001"
servicename="ROG"

---

### Post by skynoc on 2011-01-31
the dsl tab in network manager is only for wired connection , how can i make it dial through wlan0 ?

---

### Post by dineshs on 2011-04-13
Instead of running sudo pppoeconf  do```
sudo pppoeconf wlan0
```and proceed as explained [here]("http://ubuntuforums.org/showpost.php?p=10664067&postcount=15") 
Any progress?

---

### Post by redalertrox on 2012-10-13
Heres the thing i found while google'ing

set ur username : john@IBM
so this way IBM= service name.

Try it.

---

### Post by wildmanne39 on 2012-10-13
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

