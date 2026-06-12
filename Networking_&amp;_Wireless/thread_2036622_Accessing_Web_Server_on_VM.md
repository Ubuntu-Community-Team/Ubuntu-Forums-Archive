---
title: "Accessing Web Server on VM"
date: 2012-08-02
forum: Networking &amp; Wireless
---

### Post by texpat on 2012-08-02
I've set up Ubuntu in a VM (VirtualBox) and on it run an Apache2 server. On the guest OS (Ubuntu 11.04) it works fine: I go [FONT="Courier New"]**[http://localhost](http://localhost)**[/FONT] in a browser on the guest OS and get the "It works!" message.

The guest OS's network adaptor is configured as 'bridge' so that it gets a 'normal' IP address - 192.168.1.X rather than 10.0.5.1 or some such. The router's DHCP server is set up to map a fixed IP address to the guest OS's MAC. If on the host system I go to [FONT="Courier New"]**[http://192.168.1.99](http://192.168.1.99)**[/FONT] (the guest OS's IP) everything works fine.

Next, I configure the router's NAT to forward port 80 to 192.168.1.99 (the guest OS). From the host OS I go to [FONT="Courier New"]**[http://123.45.6.7](http://123.45.6.7)**[/FONT] (the router's public IP) and I promptly get "It works!" from the http server.

So far, so good. But if I try [FONT="Courier New"]**[http://123.456.6.7](http://123.456.6.7)**[/FONT] from outside my LAN I don't get through. I disabled the firewalls on both the host and guest OS-es, but that didn't solve the problem.

And now I'm confused and stuck as to how to go about this, so I kindly ask for your ideas and pointers.

---

### Post by SeijiSensei on 2012-08-02
You need to forward external port 80 on your router to port 80 on the web server.

---

### Post by texpat on 2012-08-02
SeijiSensei:
I thought this is what I did here:
> Next, I configure the router's NAT to forward port 80 to 192.168.1.99 (the guest OS).
I'm not aware of a method to specifically forward port 80 to port 80 on the server. Doesn't the web server listen on that port by default?:confused:

---

### Post by SeijiSensei on 2012-08-02
Port forwarding consists of specifying an external port that will be forwarded to an internal port.  There's no requirement that the ports be identical.  You need to tell the router both the IP address and the port of the target server.  In your router, there should be a portforwarding configuration that let's you specify the router's port to be forwarded and the IP address and port of the target machine.

---

### Post by OM55 on 2012-08-02
I can add also that some routers have settings for 'virtual server' others for 'port forwarding' and some will have both. If you have both settings on your router, the difference would be that one of them (usually 'port forwarding') will just need a LAN IP address and an external port which will forward _to the same port_ on the LAN IP. While the other (usually the 'virtual server') will also ask for the internal port number, so you can forward any external port to any internal port at the internal LAN IP address.

Since you are using Virtual Box, you may also want to make sure that the network adapter setting of your virtual machine is set to 'Bridge' and not to NAT (which is the default setting).

Trying to access the external IP from within the LAN (on your host OS) is not the same as doing it from outside the LAN, but evidently you have noticed that by now... The eventual routing will be determined by the routers algorithms. Typically, as you noticed, your traffic will be routed right away internally. In other situations (like https communication) you will most likely not be able to get through to the external IP since it may be a security issue.

Back again to your question - if you setup the network adapter of the virtual box to 'Bridge' and assigned it a fixed LAN IP, it will be treated like any other computer on the LAN and you can completely ignore the host OS. The router should forward port 80 directly to the virtual box's LAN IP.

---

