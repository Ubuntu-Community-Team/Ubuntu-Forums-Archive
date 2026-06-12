---
title: "SSHing my computer from outside"
date: 2013-01-28
forum: Networking &amp; Wireless
---

### Post by jhapk on 2013-01-28
Hello,

I just got a static IP for my office computer.  But when I am trying to ssh into it from outside using the IP, using "ssh myusername@myipaddress"  it is not working and giving me the following error:

```

ssh: connect to host 133.6.71.88 port 22: No route to host

```

Do I need to configure anything else so that I can ssh into my computer from outside? My internet is working and I checked my IP, so the IP has been configured right without error I think.

Thanks in advance for your help,
Pradeep

---

### Post by ahallubuntu on 2013-01-28
You need to forward a port through any firewalls between your office computer and the internet.  Typically you would forward port 22, the default ssh port.

It's usually a good idea to make sure you can ssh locally first while you are on the same network.  You have to install the openssh package typically on a Ubuntu installation (just install "ssh" and that should do it) to install/enable the ssh server as well.

---

### Post by jhapk on 2013-01-28
How do I forward the port?  My internet is not coming from a router. It is coming directly from an ethernet cable through the wall. I was googling but most information is about how to set it up using a router.

Also I didn't understand your second paragraph. I am on a Mac and I am able to use ssh to log on to computers outside. But most of my colleagues dont use a static ip, so I dont have any other system to check if I can login/out of other systems.

---

### Post by ahallubuntu on 2013-01-28
I'm not completely sure exactly what you are trying to do now, but without asking 20 questions, I'll give you an example.

Suppose you have a computer at your office and a Mac laptop at home.  You would like to access the office computer via ssh from home, with the Mac.

Your office has a local network of some sort, isolated from the outside world.  It has a firewall (at least one) to keep bad guys from accessing the local network.

But if your local network at the office has, say, WiFi, you could connect your Mac to it.  Then your office computer and your Mac are on the same network.  Maybe your office computer has a local IP of 192.168.1.2 and your Mac, when connected by WiFi, has an IP of 192.168.1.3 . (but the static IP is on the outside.)

Then, try doing ssh access to the office computer from your Mac (say ssh to 192.168.1.2 in the example above).  Because you are both on the same local network, there is no firewall to worry about, no port to forward.  If you can't get this to work, don't even worry about forwarding a port yet.

Once you are able to ssh into your office from your local network, then worry about forwarding a port to the office computer.

You forward the port AT THE OFFICE, not at home.  I have no idea what kind of an office you have.  Let's say it's a small office with a simple wireless router, and the WAN (internet) side of the router has that static IP you got.  The router has a firewall.  You must forward a port (perhaps 22, the standard ssh port) THROUGH that firewall, to your office computer.  There is no port forwarding to do at home where the Mac is.

Perhaps you mean something else.  I don't know what you mean exactly by "at the office."  Maybe you work in a big office and you have to ask your IT manager to forward a port through a corporate firewall.  (And maybe they'll balk at giving you 22 - maybe you'll have to use a higher port like 5000 that they don't use for anything else, if they allow you to get in at all.)  Maybe the server is on the open internet and there is no firewall protecting it, except on the server itself, in which case you'd better make sure there is a firewall running on the server.  Then you'd have to open a port (probably 22) so you can access ssh through it.

If you are trying to do something different, please explain.

---

### Post by ahallubuntu on 2013-01-28
And if it is the case where you have a simple router at the office (with a firewall), and you personally have admin privileges, you can login to the router (while at the office) and forward the port to your office computer within the router config.  For example, the IP of the router might be 192.168.1.1 - then point a web browser to [http://192.168.1.1](http://192.168.1.1) .  Or as I said, if it's a corporate office with an IT manager, you'll have to ask them to do it.

---

### Post by jhapk on 2013-01-28
Hello,

thank you a lot for the detailed reply. I use a Mac at my office and I need to access this mac from another lab in the building. 

Your reply did explain a lot of things. I googled more using "forwarding ports in mac" and I managed to figure it out. Now I am able to ssh in my Mac from outside machines.

I appreciate your detailed replies a lot.
Thanks again.
Pradeep

---

### Post by jhapk on 2013-01-28
Hello,

thank you a lot for the detailed reply. I use a Mac at my office and I need to access this mac from another lab in the building. 

Your reply did explain a lot of things. I googled more using "forwarding ports in mac" and I managed to figure it out. Now I am able to ssh in my Mac from outside machines.

I appreciate your detailed replies a lot.
Thanks again.
Pradeep

---

