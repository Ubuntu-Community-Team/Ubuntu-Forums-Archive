---
title: "Proxy Update"
date: 2010-08-31
forum: Networking &amp; Wireless
---

### Post by stefanog on 2010-08-31
Hi! I installed Ubuntu on a machine of our laboratory. Since we are at the university connections may pass through a proxy (whose url we ignore). All things concerning system update are nearly unusable. Several posts say to add in apt strings like .. $ export http_proxy="http:..." $ export ftp_proxy="http:..." but I don't know the url proxy at all.  

Firefox is set to "Direct internet connection" and all work well. 
In Windows all connection properties were set to "automatic" and updates were ok. 
Is there a way to have an automatic recognition by apt?

---

### Post by uberlinuxnerd on 2010-08-31
Hi there,

One route, and it is the route I would take is setting up a zeroconfig caching server with squid. The clients will use this if it is available with out needing any configuration solving your problem in hand.

Since lucid this has been super easy.

On the server:
```
sudo apt-get install squid-deb-proxy avahi-utils
```On the clients:
```
sudo apt-get install squid-deb-proxy-client
```This is great, as nobody cares if the caching server isn't there or not (e.g. Laptops and the like!) so things in theory should never break.

Hope this helps

---

### Post by stefanog on 2010-08-31
uhmmm... sorry for ignorance but does this

On the server:
sudo apt-get install squid-deb-proxy avahi-utils

mean i need to install something on the university's server?? I don't even know it. And for sure I don't have any permission to do such things.
I have permissions only on the client machine.

---

### Post by BkkBonanza on 2010-08-31
If your browser works with a direct connection then then any proxying is being handled upstream, not via your settings. This means that other programs would work the same way unless ports are being blocked. It's fairly common for organizations to block other than, say 80 and 443, for web traffic, to prevent users from doing weird stuff.

ftp for example uses 20 and 21. If they are filtered/blocked then that won't work.

You could try asking if ports can be opened to facilitate updates but my guess is they aren't going to do that nor allow you to run a proxy anywhere inside the network.

This leaves you with using an outside proxy configured to listen on 80 or 443. Often people will run a ssh server listening on 443 as a secure proxy on their home machine or any other place not-blocked. Since 443 isn't blocked you can then configure your machine to get to that proxy and enable all traffic through that. Doing this with ssh is very easy and by far the quickest way to go since ssh is already installed on Ubuntu and sshd (the server) easily installed on any home/outside machine.

If this interests you then there are many tutorials and posts here about how to config ssh as a proxy. Or ask me, and I'll describe it again. It's certainly much easier than setting up squid and more flexible for this type of purpose.

---

### Post by stefanog on 2010-08-31
i've set localhost and 443 port in preferences>proxy settings
and at this point it can download at a nearly decent speed.

let's try your idea anyway.. i've just googled and there is a ton of stuff. have you a specific link? Sorry but i don't have much time and i need something that "just works".

---

