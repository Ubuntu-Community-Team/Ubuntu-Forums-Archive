---
title: "another wired connection problem, won't always connect"
date: 2010-09-03
forum: Networking &amp; Wireless
---

### Post by badbradmx on 2010-09-03
ive just installed 10.04 on a mates computer, and the wired connection is being very touchy, it wont connect then after a couple restarts it might connect. once ive somehow got it to connect it works flawlessly no drop outs or anything. dont wanna give this back with this kind of problem, any ideas?

---

### Post by MaindotC on 2010-09-03
You should try and narrow down where the problem lays because it could be either the ubuntu machine or whatever device is connected to it.  Is it connected to an access point?  If so, is the AP configured properly or are there any settings (like mac filtering or 802.1x) that could cause a disruption of service?  Can you try connecting it to another device - be it an access point or other machine and see if connectivity works between them?

---

### Post by badbradmx on 2010-09-03
basically i have a whole host of PC's connected to the net and each other via a wireless router.

i have an ubuntu machine, vista, XP, windows 7 a samba server. its this machine and its settings, ive not had to fiddle with the others, and i dunno where to start to debug this

---

### Post by MaindotC on 2010-09-03
> **badbradmx said:**
> and i dunno where to start to debug this

I told you where to start.

---

### Post by badbradmx on 2010-09-03
but those arent the problems, the router is not at fault, i know that for a fact. it just wont connect every time it boots. wont connect to any other PC on the network. just comes up with "you are not online, connection disconnected"

---

### Post by MaindotC on 2010-09-03
I cannot help you further.  Good luck!

---

### Post by Iowan on 2010-09-03
On-board a little late... 
What is the router (brand, etc.)? I presume you're trying to get DHCP address? When it won't connect, try **sudo dhclient** - post results.

---

### Post by badbradmx on 2010-09-04
guys, and girls, maybe, i appreciate the responses but he was round and needed the computer so i had to bite the bullet and install windows, without the time to troubleshoot i had no alternative. 

But...i may be returning to this post in a couple months as we have almost an identical PC (6 months difference but same model) after the paid for AV runs out, may encounter the same problem

---

### Post by smartgilli on 2010-09-08
hi, ):P
Try this and let me know if it had helped . 

[http://ssatish.wordpress.com/2010/08/22/wired-connection-disconnected/](http://ssatish.wordpress.com/2010/08/22/wired-connection-disconnected/)

-
Satish

---

