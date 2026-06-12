---
title: "Networking over a wireless bridge"
date: 2010-03-15
forum: Networking &amp; Wireless
---

### Post by TheAnarchitect on 2010-03-15
I just installed Karmic Koala on my desktop computer, and have run into an issue. My internet connection is made through a linksys wrt54g that I have turned into a wireless bridge with 3rd party firmware. The other end is the wireless router that came from At&t. 

The problem is, every so often if the internet is idle long enough, it will drop the connection. I have been unable to reconnect. 

Previously I was using a version of Puppy Linux, and simply going through the connection wizard would renew the connection. specifically, hitting the "Auto DCHP" button would do it. I have not figured out how to do this with networkmanager yet. 

Complication 1: Ubuntu seems to be treating this as a wired LAN rather than a wireless network. I do not get any info through networkmanager on the wireless, just the LAN to the router. 

Complication 2: The default ip address for accessing the router's control panel gets me the control panel for the AT&T wireless router, not my Linksys bridge. I don't know what, if any, ip will get me to that control panel and need a way to find out. I set this bridge up late night about 8 months ago and don't have any notes. 

My current Kludge: As of now whenever my internet goes down, I am shutting down, booting into  puppy to use their network configuration wizard, then booting back into ubuntu. It seems to hold whatever settings are changed, and the internet works again for a day or so. This is a pain in the butt, though, and I could really use a way to fix this without rebooting. I'm kinda at the end of what I can figure out alone.

---

