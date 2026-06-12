---
title: "how can I connect to access point from command line"
date: 2010-04-04
forum: Networking &amp; Wireless
---

### Post by JUSTINBEAIRD on 2010-04-04
I have an old laptop that the screen dont work on anymore so I thought I would put it to use as a web server and a transparent squid proxy maybe i will have it manage dns so i am wondering how  can i connect to the ap using the command line 

i plan on using ubuntu server with no gui and when i reboot will it auto connect the the ap?
if not how can i accomplish that

my network is WPA2/AES

---

### Post by gzarkadas on 2010-04-04
I haven't actually done it, but I believe the following will solve your problem:

[LIST]
[*]Use  the `iwconfig' tool to set-up your wireless connection from the command line.
[*]Use `ifup' (at the command line or at a startup script) to activate the wireless connection.
[/LIST]

---

