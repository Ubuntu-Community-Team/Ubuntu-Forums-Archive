---
title: "[SOLVED] How to setup my nas to be ftp server?"
date: 2008-12-21
forum: Networking &amp; Wireless
---

### Post by geekyhawkes on 2008-12-21
Hi guys;

i have recently replaced my freecom nas with a buffalo and was thinking about using the freecom drive as an ftp server.  The nas itself supports ftp with user accounts etc, but i am unsure exactly the steps required to have it accessible from the "outside" world. 

My understanding is that I need to use my router (orange livebox) to forward the ftp requests.  The nas ip address is clearly only an internal ip address so i am guessing i would need to use the routers IP address and then setup some kind of port forwarding (80?) to the nas.  

Are there any other obvious (or not) steps i am missing?

Thanks.

---

### Post by Iowan on 2008-12-21
FTP is usually port 21, but it's notoriously insecure (passwords transmitted in plain text).  If the NAS will support it, consider going next door (so to speak) to port 22 and SSH.  Even more secure is to move it to non-standard port (eg. 2200).

---

### Post by geekyhawkes on 2008-12-21
Thanks.  I realise this might be specific to my nas, but how do i tell it which port to listen on?  I have found a port forwarding screen on my router setup so this should allow me to forward data to the nas

---

### Post by Iowan on 2008-12-21
I presume there's an option in a setup screen or configuration file that lets you choose the port... but, as you mentioned, "this might be specific to my nas".  I haven't done port forwarding, but it might be possible to forward from a nonstandard port on your router to a standard port on your server (eg. forward port 2200 on the router to port 22 on the server.)  From outside the network, you'd connect to port 2200.  The other trick is gonna be the external address.  Unless you have a static IP address, you'll need a service like **no-ip** (or dyndns?) to help you find your network in the Internet ocean.

---

### Post by geekyhawkes on 2008-12-22
Thanks very much.  My router does seem to support port forwarding as you described above.  I have a static IP as long as my router stays connected so it should work for most of the time without no ip.  

Thanks for your help

SOLVED

---

