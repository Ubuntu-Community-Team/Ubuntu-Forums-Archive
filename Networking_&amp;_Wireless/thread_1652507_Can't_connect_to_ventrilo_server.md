---
title: "Can't connect to ventrilo server"
date: 2010-12-25
forum: Networking &amp; Wireless
---

### Post by CloudGorilla on 2010-12-25
** Edit: I CAN connect from my linux box with the "Mangler" client**, so I  think this is just a basic network port forwarding/firewall issue.   Also I don't think the router is the problem, since the server was OK on  Windows, and the laptop is on the same LAN anyway. 

Any advice on what to check to see if I have some sort of firewall enabled on my stock 10.04 installation?

**Edit 2: It just magically started working.  I don't know how or why.. Man, I hate ventrilo : /**

--------------------

Hi guys, I just set up a clean installation of Ubuntu 10.04, and I'm trying to get my ventrilo server back up and running so I can chat with my friends

I followed the instructions at this page:
[http://rocketeerbkw.com/content/installing-ventrilo-server-ubuntu-910-karmic-koala](http://rocketeerbkw.com/content/installing-ventrilo-server-ubuntu-910-karmic-koala)

and didn't run into any trouble during them, but it seems like I'm missing something, since the server says it's running but I can't actually connect to it from my windows laptop

Here's the output from the status command:
> 
cloud@gorilla1:/etc/ventrilo$ sudo /etc/init.d/ventrilo status
 * Vent is running (pid 4244).
 * NAME: Elite Pro Vent
PHONETIC: One Three Three Seven
COMMENT: 
AUTH: 0
MAXCLIENTS: 8
VOICECODEC: 0,GSM 6.10
VOICEFORMAT: 3,44 KHz%2C 16 bit
UPTIME: 2
CLIENTCOUNT: 0I'm not really sure where to go from here.  I was able to telnet in to port 3784 on localhost from my linux box, but telnet connections are refused from my windows laptop

I tried "sudo ufw disable" but it didn't change anything

---

