---
title: "I need to connect remotely to another Ubuntu PC over the internet!"
date: 2009-02-12
forum: Networking &amp; Wireless
---

### Post by Rytron on 2009-02-12
Hi. Can I use Terminal Server Client to connect to another Ubuntu PC over the internet? Would I use the real IP address(from [http://www.cmyip.com/](http://www.cmyip.com/)) of the PC to connect to?

---

### Post by Rytron on 2009-02-12
I tried to get port forwarding done before but no luck. Here (image attached) is a shot of my router port forwarding page.

Not sure exactly what to do next for this particular thread query.

---

### Post by Fire_Chief on 2009-02-12
Yes, you would use the real IP. The port forwarding would depend on how you want to connect to the Ubuntu PC. If you just want cmd line access, you can use SSH which would be TCP port 22. If you want GUI access, you would use VNC which is TCP port 5900.

---

### Post by ddmdllt on 2009-02-12
You may also have to check the NAT/router settings of the computer you are trying to connect to.

Depending on your internet connections speeds, VNC may be usable or not.

ssh (remote shell in text mode) works even with low bandwidth connections.

---

### Post by Rytron on 2009-02-12
Thank guys. I will hope to try this once I manage to forward ports on my wireless router. I suppose a good way to test would be port forwarding 5900 on my router from my desktop PC and try connecting to my laptop which is also connected to the same wireless router via Terminal Server Client with the VNC protocol.

---

### Post by Fire_Chief on 2009-02-13
That will be a good test only if you connect to a different wireless network and then try to reach your desktop PC over the Internet. Testing from the local wireless on your LAN does not make use of the port forwarding setup.

Cheers!

---

### Post by issih on 2009-02-13
Just to be clear you need to enable port forwarding on the router that the machine you are connecting to uses to access the internet, not your router. I think things should just work at your end, although now I think about it I wonder how NAT works outside the http protocol.

When you ask for a web page or whatever from behind a router, the router knows you asked for it, so it knows which connected machine to send those data packets to when they come in from the internet.

If, however, the data coming in from the internet was not requested from a machine inside the routers network, the router doesn't know where to send it, so it is just dumped.

Port forwarding simply tells the router to send any unsolicited data recieved on a specific port/range of ports onto a specific machine on the internal network.

Therefore, what you need is to have the router of the machine you are connecting to know how to deal with traffic coming in from your pc, and how to send it to the machine you actually want to connect to.

Be aware that you should consider using a none standard port for ssh access and you should make sure you use strong passwords and denyhosts to lock down the security of things a bit.

Hope that helps, and sorry if I just told you lots of stuff you already knew :)

---

### Post by ddmdllt on 2009-02-21
> **issih said:**
> I wonder how NAT works outside the http protocol.

Generally, NATs don't care about HTTP, they handle the same way nearly all outgoing TCP connexions. (One exception may be FTP : some NATs read/write inside the packet content to make this protocol working)

---

