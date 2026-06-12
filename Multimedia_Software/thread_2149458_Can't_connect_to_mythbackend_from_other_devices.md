---
title: "Can't connect to mythbackend from other devices"
date: 2013-05-28
forum: Multimedia Software
---

### Post by kr651129 on 2013-05-28
Ok, I gave mythtv one more shot and I've been able to get it working locally.  While setting up the backend it gives me the choice to use an IP other than localhost.  I kept it localhost because it's my understanding that is the correct setting if it's the only backend, which it is.

The problem is I can't connect to it from xbmc on my pi (no errors, just not connecting) and I can't connect to it from any of the mythtv apps I've downloaded on my android tablet.  I've tried passing thoes apps and xbmc the IP of my ubuntu machine that mythtv is on.  I get no errors other than it cant find the backend or it times out.

On one of the apps it gives me the option to connect via ssh, since this is all behind my firewall I don't need that but I thought I'd try anyway.  The backend console says the they speak different protocols.  I'm not to worried about this since I don't need to connect via ssh anyway.

This setup is all behind a cisco home router, mythtv is running on Ubuntu 13.04.  Can someone please help guide me in the right direction with this problem, I'm really stumpped.  I can ssh into my Ubuntu machine using putty fine and my intranet website can be accessed by all clients so I'm not really sure where to go here.

I did compile mythtv from source, maybe I didn't pass it an argument that I should have at configure?

Thanks!

---

