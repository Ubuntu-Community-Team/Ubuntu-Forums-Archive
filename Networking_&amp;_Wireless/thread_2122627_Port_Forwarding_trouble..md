---
title: "Port Forwarding trouble."
date: 2013-03-05
forum: Networking &amp; Wireless
---

### Post by Dazedndconfused on 2013-03-05
Let me start off by saying my OS is Ubuntu 12.10 and that I have very minimal experience with Linux.

Ok so the problem I have run into is I am trying to forward a port. Now I went into my router setting and forwarded the proper port. I changed over the Private IP to the IP for the Ubuntu OS (I previously forwarded the port when I had windows and it worked. So all i had to do was make it forward the same port for Ubuntu.)

Now my question is is there an internal firewall on Ubuntu that is stopping this port from being forwarded?

The error I get when I check the port is connection refused. So its open but something is blocking it.

If there is an internal firewall, how do i allow the access in and out of the port.

---

### Post by papibe on 2013-03-05
Hi Dazedndconfused.

There's no firewall by default. However, there must be a service (program) that is listening to the port in order to get a connection.

What service are you trying to set up?
Have you try accessing it locally first (LAN name and address), so you know it is well configured?

Note, that it is usually not possible to access your public name or IP from the LAN itself. In order to properly test remote access, you need to use your phone network service (not connected to WiFi), or form outside: public library, a friend's house, etc. 

Let us know how it goes.
Regards.

---

### Post by Dazedndconfused on 2013-03-05
Well I'm trying to run a Minecraft server. Everytime I launch the server it throws me an error "Cannot Bind Port" then asks if there is already a server running on this port. So i checked to make sure the port is open on my router and it is. There is nothing that is listening on the port 25565 and nothing can bind to it. So I was curious as to if there was an equivalent to Windows Firewall in linux... I'm boggled. I guess I will continue to try to figure something out. Thanks for the quick response.

---

### Post by SeijiSensei on 2013-03-05
You can do a quick check to see if you have any iptables firewall rules installed by running:

```
sudo iptables -L -nv
```

That will list all the rules in effect, if any.

What if you bind the Minecraft server to a different port?  Port forwarding doesn't require that the target port be the same as the external port.  You could forward port 12345 to 54321 if you want.  Binding the server to a different port should eliminate the "cannot bind" error if there is something else listening there.  If the problem doesn't go away, then I'd bet there's a firewall in operation that you are unaware of.

---

### Post by Dazedndconfused on 2013-03-05
There has to be a firewall in operation somewhere because no matter what port I try to bind it on it still fails. How would I allow the port through the firewall?

---

### Post by papibe on 2013-03-05
Don't bind your server to a particularly IP. If you leave it blank, it would bind to all IPs available:
```
ip=
```
Let us know how it goes.
Regards.

---

### Post by Dazedndconfused on 2013-03-05
> **papibe said:**
> Don't bind your server to a particularly IP. If you leave it blank, it would bind to all IPs available:
```
ip=
```
Let us know how it goes.
Regards.

It works fine when I run it like that. But when I put in my IP so others and myself can connect it refuses to bind to a port.

---

### Post by papibe on 2013-03-05
Try connecting locally using that configuration. If it works, tell your friend to try to connect also.

Let us know how it goes.
Regards.

---

### Post by Dazedndconfused on 2013-03-05
There is no way he can connect because it doesnt have a registered ip. you can only connect through localhost without putting an IP in the configuration

---

### Post by Dazedndconfused on 2013-03-05
Can someone mark this as solved please? I either cant do it or I'm too stupid to figure it out :(.... Thanks for all the help

---

