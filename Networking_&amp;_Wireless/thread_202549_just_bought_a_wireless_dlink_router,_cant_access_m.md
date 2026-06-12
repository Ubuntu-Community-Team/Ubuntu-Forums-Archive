---
title: "just bought a wireless dlink router, cant access my web server..."
date: 2006-06-23
forum: Networking &amp; Wireless
---

### Post by dragonflyFZX on 2006-06-23
hi,

i just added a wireless d-link router to my " home network ".  Now i can not access the web server i set up anymore.  Here is the setup.  I have a dsl ethernet router connected to the phone line (thompson speedtouch), which used to be connected to a computer running apache.  The router gets an ip from the isp dynamically, so i had to set up a NAPT rule to forward port 80.  So now i added the router between the dsl router and the apache server.  Can someone plz explain me what settings to adjust in the dsl router, d-link router or my server to open up port 80 again???

---

### Post by Kulgan on 2007-03-26
if you are still wondering (you probably found a solution somewhere, so just for the record, then)...

1. Run "ifconfig", or "ipconfig" for windows (do this from the machine that is running the server). In linux there is a line under the apropriate address that says "inet addr: " followed by an IP. For windows, it is something similar, and should be pretty obvious. In either case, this is your internal IP.

2. Go to the router's IP (usually 192.168.0.1 or 192.168.1.1 by default). Click Advanced->DMZ. Click "enabled" and enter the Internal IP of the server. Click apply, save all, or whatever seems appropriate. 

That's it, really, so long as your modem is set up correctly (as far as I know, the NAPT should be set to go to the router's IP, which then uses the DMZ feature to send it on to the server.) 

-K

---

