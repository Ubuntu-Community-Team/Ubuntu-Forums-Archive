---
title: "What is wrong with netstat?"
date: 2013-02-05
forum: Networking &amp; Wireless
---

### Post by lynxus on 2013-02-05
Hi Guys,

Question...

How on earth do I view listening ports and est ports?
Netstat on ubuntu is giving completely different output than any other distro i have used?

( Cont copy and past because its via a hyperv console.. )

Anyway, 
It looks like:
unix 4 [] DGRAM /dev/log

It seems to show internal connections?

How do I see a normal netstat that outputs "normally" lol?

---

### Post by PowerBarry43 on 2013-02-05
Hi

Try running

```
netstat -l
```

for all listening ports

```
netstat -a

```
for all ports.

you can also add -t or -u for only tcp or udp.

Alternatively if you just want to know which ports are open install nmap and portscan yourself.

```
sudo apt-get install nmap

nmap localhost
```

Hope this helps!

Barry

---

### Post by The Cog on 2013-02-05
man netstat will give you the details, but:
netstat -t : shows only tcp connections
netstat -u : shows only udp connectons
netstat -l : shows only listening ports
netstat -lntua : shows all listening and connected tcp or udp ports with numeric addresses

---

### Post by lynxus on 2013-02-05
> **PowerBarry43 said:**
> Hi

Try running

```
netstat -l
```

for all listening ports

```
netstat -a

```
for all ports.

you can also add -t or -u for only tcp or udp.

Alternatively if you just want to know which ports are open install nmap and portscan yourself.

```
sudo apt-get install nmap

nmap localhost
```

Hope this helps!

Barry


Nope doesnt work.
I just see the unix sockets with no port details and a whole bunch of dbus stuff.

It looks like this: ( Certainly nothing like what im used to seeing... )

unix 3 [ ] STREAM CONNECTED 9513 
unix 3 [ ] STREAM CONNECTED 9524 @/tmp/dbus-QAwlQdsJQE
unix 3 [ ] STREAM CONNECTED 9512 
unix 3 [ ] STREAM CONNECTED 9486 @/tmp/dbus-QAwlQdsJQE
unix 3 [ ] STREAM CONNECTED 9485 
unix 3 [ ] STREAM CONNECTED 9484 /tmp/.esd-1000/socket
unix 3 [ ] STREAM CONNECTED 9483 
unix 3 [ ] STREAM CONNECTED 9481 @/tmp/.ICE-unix/1747
unix 3 [ ] STREAM CONNECTED 9480 
unix 3 [ ] STREAM CONNECTED 9482 /tmp/orbit-shawnc/linc-732-0-3edd427234522
unix 3 [ ] STREAM CONNECTED 9479 
unix 3 [ ] STREAM CONNECTED 9477 /tmp/orbit-shawnc/linc-76d-0-394aba96acf46
unix 3 [ ] STREAM CONNECTED 9476 
unix 3 [ ] STREAM CONNECTED 9478 /tmp/orbit-shawnc/linc-76b-0-14ac964fad8a9
unix 3 [ ] STREAM CONNECTED 9475 
unix 2 [ ] DGRAM 9462

I issue,
netstat -t
-a
whatever and its just streams of unix sockets.

I normally issue netstat -tunap on any server. yet this LTS server is odd..

---

### Post by lynxus on 2013-02-05
Found the issue.

Turns out if the firewall hasnt got it allowed out, then it doesnt show!? 

Go figure.

_g



> **lynxus said:**
> Nope doesnt work.
I just see the unix sockets with no port details and a whole bunch of dbus stuff.

It looks like this: ( Certainly nothing like what im used to seeing... )

unix 3 [ ] STREAM CONNECTED 9513 
unix 3 [ ] STREAM CONNECTED 9524 @/tmp/dbus-QAwlQdsJQE
unix 3 [ ] STREAM CONNECTED 9512 
unix 3 [ ] STREAM CONNECTED 9486 @/tmp/dbus-QAwlQdsJQE
unix 3 [ ] STREAM CONNECTED 9485 
unix 3 [ ] STREAM CONNECTED 9484 /tmp/.esd-1000/socket
unix 3 [ ] STREAM CONNECTED 9483 
unix 3 [ ] STREAM CONNECTED 9481 @/tmp/.ICE-unix/1747
unix 3 [ ] STREAM CONNECTED 9480 
unix 3 [ ] STREAM CONNECTED 9482 /tmp/orbit-shawnc/linc-732-0-3edd427234522
unix 3 [ ] STREAM CONNECTED 9479 
unix 3 [ ] STREAM CONNECTED 9477 /tmp/orbit-shawnc/linc-76d-0-394aba96acf46
unix 3 [ ] STREAM CONNECTED 9476 
unix 3 [ ] STREAM CONNECTED 9478 /tmp/orbit-shawnc/linc-76b-0-14ac964fad8a9
unix 3 [ ] STREAM CONNECTED 9475 
unix 2 [ ] DGRAM 9462

I issue,
netstat -t
-a
whatever and its just streams of unix sockets.

I normally issue netstat -tunap on any server. yet this LTS server is odd..

---

