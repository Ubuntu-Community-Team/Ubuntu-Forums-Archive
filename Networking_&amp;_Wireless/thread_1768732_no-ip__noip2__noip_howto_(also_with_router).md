---
title: "no-ip / noip2 / noip howto (also with router)"
date: 2011-05-27
forum: Networking &amp; Wireless
---

### Post by sam1948 on 2011-05-27
first of all
```
sudo apt-get install build-essential
```

go to noip website and download th linux client
extract it and open a terminal in the extracted folder.
now run these:
```
make
```
```
sudo make install
```
```
sudo chmod 770 /usr/local/etc/no-ip2.conf
```
(u r allowed to think about better permissions)

to see the help:
```
noip2 -h
```

u can run after computer startup manually from command line or add it System-->Preferences-->Startup Applications.
the command is:
```
noip2
```
-----------------------------------------------------------
if running behind a **router**:
the command is:
```
noip2 -F
```
(this will tell the client not to send your internal LAN-ip)

in the router, in order to tell it what to send to your computer in the LAN (even if you'r the only one there) 
set up a static ip in the LAN to your computer. and then
do one of the following:
 - add you'r computer to DMZ
OR
 - specify specifically port-forwarding per a process.
OR
 - specify server applications for your LAN-ip in th router (probably router dependent)

enjoy(;

---

