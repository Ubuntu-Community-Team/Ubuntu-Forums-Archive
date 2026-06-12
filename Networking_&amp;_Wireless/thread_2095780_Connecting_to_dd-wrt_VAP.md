---
title: "Connecting to dd-wrt VAP"
date: 2012-12-17
forum: Networking &amp; Wireless
---

### Post by highaltitude on 2012-12-17
So my apt offers free wireless internet but to allow sharing between pcs I have a cisco router running dd-wrt as a repeater with a virtual ap.

I have no problem connecting with win7 or android but my linux systems cannot connect. I have tried ubuntu 12.04, backtrack 5 and mint 13. All with no luck connect to the router. 

Hopefully someone would have encountered this before. I can provide more information if needed from the ubuntu 12.04 system

edit: all computers can connect directly to the apt wireless

---

### Post by synapsys on 2012-12-17
I am curious, why do you need the Cisco? Why are you using it as a repeater?

---

### Post by highaltitude on 2012-12-18
i am using the repeater for internet but also allow for media streaming to my xbox and file sharing. it seemed like the best way to meet my needs. is there a better way?

---

### Post by synapsys on 2012-12-18
I can't say for sure without knowing more about your situation. You say all clients can connect directly to the apt wireless, but that it doesn't allow for sharing? Is it somehow segmented by subnets? Are you only allowed to connect one device at a time? 

Wireless is a half-duplex technology meaning that every repeater you use effectively cuts your bandwidth in half. It's best not to use them unless you absolutely have to.

---

### Post by highaltitude on 2012-12-18
connecting directly to the apt wireless does allow for sharing but it is a single pw for the 8 apartments. i am trying to avoid sharing with everyone else. 

the router used for the apt is a wrt120n

---

### Post by synapsys on 2013-01-05
What encryption are you using? It could be that the driver you're using in Linux doesn't support the encryption your're using.

---

