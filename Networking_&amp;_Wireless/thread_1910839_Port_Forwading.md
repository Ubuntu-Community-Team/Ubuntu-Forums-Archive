---
title: "Port Forwading"
date: 2012-01-17
forum: Networking &amp; Wireless
---

### Post by Amici343 on 2012-01-17
Hey everyone,

I'm trying to forward port 22 so I can remotely SSH into my home computer.

I've set everything up to no avail, but after a lot of headache I'm pretty sure that my apartment complex is routing all of us through their modem (which is acting like a router as well) so I can't properly port forward. 

Is there any way I can forward my port without having to gain access to their modem/router and mess with the settings (which they'd probably see and remove anyway)

---

### Post by Iowan on 2012-01-17
Perhaps it's my limited experience in this area, but without access to the router, I don't see how you could set up port forwarding. :(

---

### Post by SeijiSensei on 2012-01-17
> **Amici343 said:**
> I'm pretty sure that my apartment complex is routing all of us through their modem (which is acting like a router as well) so I can't properly port forward.

One way to check this is to install the "traceroute" program, then issue the command "traceroute -n www.google.com" and see what intermediate routers are listed.  If there's a router handling all the traffic for your complex, you should see it in one of the initial "hops".  (The "-n" switch tells traceroute to report IP addresses and not bother trying to resolve them into hostnames.)

If you don't have control over the router, port forwarding is pretty much out.  In the unlikely instance that you also have access to another machine connected directly to the Internet, you could create a static-key OpenVPN tunnel between your home computer and the remote server.  You could then SSH to the remote server and have it forward the traffic to your home machine.

---

### Post by shepherdzw on 2012-01-18
> **Amici343 said:**
> Hey everyone,

I'm trying to forward port 22 so I can remotely SSH into my home computer.

I've set everything up to no avail, but after a lot of headache I'm pretty sure that my apartment complex is routing all of us through their modem (which is acting like a router as well) so I can't properly port forward.

Is there any way I can forward my port without having to gain access to their modem/router and mess with the settings (which they'd probably see and remove anyway)

NO ways if the router has a firewall.Communicate with the owner or administrator of your gateway/router to help you achieve this. Otherwise forget and smile :-)

---

### Post by Lars Noodén on 2012-01-18
From the inside, you can also do a scan of port 22 using:
[http://canyouseeme.org/](http://canyouseeme.org/)

That will at least tell you if there is a filter in the way or not.  If it is being blocked, then you'll have to work out an arrangement with the administrator of the filter.

---

### Post by Amici343 on 2012-01-18
I was afraid that was the case :(

I tried accessing port 22 on that website Lars, and it says connection refused which is what I get when I try to remotely SSH into my computer. So I'm guessing their modem/router has a firewall and won't let me access port 22.

Thanks for the help. I guess I'll try calling my leasing office. Hopefully they have an IT guy who is in a generous mood

---

