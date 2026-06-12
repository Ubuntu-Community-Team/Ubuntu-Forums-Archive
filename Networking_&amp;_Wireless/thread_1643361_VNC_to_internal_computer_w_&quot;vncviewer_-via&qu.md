---
title: "VNC to internal computer w/ &quot;vncviewer -via&quot;?"
date: 2010-12-11
forum: Networking &amp; Wireless
---

### Post by astroryan7 on 2010-12-11
I'm trying to VNC into a computer that does not broadcast it's ip address. I can ssh into it though, for example, by first ssh'ing into a computer that does broadcast it's ip address.

Someone told me the following would work:
```
vncviewer -via user@externalhost internalhost
```

but I get:
```
channel 3: open failed: connect failed: No route to host
vncviewer: VNC server closed connection
```

Googling has not helped. Any suggestions appreciated. Thanks.

---

### Post by diablo75 on 2010-12-11
When you SSH in, are you using the IP address or a hostname?

---

### Post by CharlesA on 2010-12-11
I'm guessing they are trying to connect to it from outside the local network.

Just use an SSH tunnel.

---

### Post by astroryan7 on 2010-12-12
Ah, well, the computer I want to eventually VNC to only has an IP address (not on DNS), and you can't access it from say home (call it a work computer). Call this "computer1".

But I can access another computer at work (call this "computer2") from home, so that's why the guy told me to use the -via option for vncviewer.

I can get to computer1 this way:
```
ssh user2@computer2 (enter password)
ssh user1@computer1 (enter password)
```

But typing:
```
vncviewer -via user2@computer2 computer1
```

doesn't work (I get the error message posted earlier). Again, computer1=IP address and computer2=hostname.

Thanks again.

---

### Post by CharlesA on 2010-12-12
Just create a SSH tunnel to whatever machine you want to connect to with VNC.

See here: [http://www.cyberciti.biz/tips/tunneling-vnc-connections-over-ssh-howto.html](http://www.cyberciti.biz/tips/tunneling-vnc-connections-over-ssh-howto.html)

---

