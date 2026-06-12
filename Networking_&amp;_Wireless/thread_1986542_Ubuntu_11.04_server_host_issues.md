---
title: "Ubuntu 11.04 server host issues"
date: 2012-05-25
forum: Networking &amp; Wireless
---

### Post by vjb1 on 2012-05-25
Hi all,

I'm trying to get a server live, it's connected via ethernet to a router in my home.  I was under the impression my router needs to have a static ip, so I went and got one.  My server machine has been added via mac address to the routers dhcp reservation list, meaning it should also maintain a constant ip within my local network.

I installed the gnome tool thing for ubuntu 11.04 so that I have the option System>Administration>Network, meaning I can attempt to deem my machine a server.

When I acquired the routers static ip, I also received a host name.  In the newly installed 'Network' menu tool, I input the routers host name in the 'Host name' space but there's also a prefilled 'Domain name' space and no matter what I do, the 'Domain name' space is overwritten with the default upon machine reboot.  I believe this is because the router is DHCP.

I have port forwarding working properly on my router and know this because I can ssh into the host name (static ip) of the router and am forwarded to the desired machine, my server.

No matter what I do the server does not function for the world, as it's purpose is to allow users to login to a site it hosts from anywhere.  Please help!

---

### Post by papibe on 2012-05-25
Hi vjb1.

I'm a little confused. Are you saying that both the router and your server have the same hostname? That wouldn't be good.

So are able to ssh inside your network to the server, but from the outside? Is that it?

Regards.

---

