---
title: "Connected to network, but internet not working"
date: 2010-07-17
forum: Networking &amp; Wireless
---

### Post by AfrikaDietmar on 2010-07-17
Hi,

unfortunately my phone line is not having any pulse nor dsl so i tried to go online in a cafe on wlan but whenever i tried to connect to their router i had the message "disconnected to wlan". So i tried at a friends place to go online with his router by plugging in his cable. The only way i was able to connect to the router was to set on ipv4 under method "shared to other computers" but i'm not able to connect to internet. Any idea what might be the problem ?

---

### Post by AfrikaDietmar on 2010-07-17
Hi, problem solved after trying for the whole day. 
Managed to make wireless and with cable connection work.
Used is a modem/router and wireless device connected to the modem router. Nowadays you will usually have it all in one device.

Method applied for wireless:

Right clight on network connection in tab. (There where you have your WLAN connection or wired connection symbol.)

Went on "Edit Connections"

Went on Wireless

(For me a connection was already showing, so i didn't click on Add)

Click on Edit of the shown connection.

Choose Mode: Infrastructure (I tried Ad-hoc before and it didn't work, no idea what it means.)

Wireless Security: in my case it was "None". You will need to check how the router is setup. 

IPv4, there click on Method "Manual", then for Addresses go on Add
There i added my IP address, i just choose something random like
192.168.0.26

Netmask
255.255.255.0

Input gateway ip
You will get that from the routers settings.

Input DNS server ip
You will get that from the routers settings.


Set IPv6 on ignore.

Similar work around for wired connection. That worked for me.

Now what remains to be tested is how will i connect in a wifi coffee shop, if simply setting IPv4 on "shared computers" will work, or if i will need to input all their IP addresses, usually that would be overkill questions for the workers in coffee shops (am not talking of internet cafes.) Anybody has some experience with wifi in coffee shops ?

---

### Post by naveen9885 on 2010-07-28
Help me with this issue in this [thread]("http://ubuntuforums.org/showthread.php?t=1537782") pls

---

