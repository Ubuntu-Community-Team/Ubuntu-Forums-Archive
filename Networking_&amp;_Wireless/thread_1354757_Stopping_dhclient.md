---
title: "Stopping dhclient"
date: 2009-12-14
forum: Networking &amp; Wireless
---

### Post by MarkMcLT on 2009-12-14
I am trying to change a machine running karmic behind a router to use a static ip address - I edited /etc/network/interfaces to define the local ip address, gateway etc, and ran '/etc/init.d/networking restart'. The machine successfully changed to the ip address I specified - as confirmed with ifconfig.

However I notice that dhclient is still running, and I'm guessing that at some point it's going to pull a new address off the router and overwrite what I've just done. I believe this actually happened when I was trying the same thing yesterday - although in that case I had actually disabled dhcp on my router as well and although initially everything was working fine, at some point the interface just stopped working completely for no (at the time) obvious reason.

So my question is whether there is a safe way to stop dhclient. I tried killing the process from the command line, but it automatically started itself right back up again, and in the process actually did what I had feared - went and overwrote the static ip address with a new one from the router. 

Is there a recommended way to do this?

---

### Post by MarkMcLT on 2009-12-14
BTW, I just tried commenting out the 'request' lines in /etc/dhcp3/dhclient.conf and killing dhclient. However it again restarted itself and overwrote the static ip address as before.

I also notice there is a network admin gui under the preferences menu that has an option for changing the IPv4 method from DHCP to manual. That sounds like it might be helpful, but I'm reluctant to use it without understanding what it's actually doing under the covers.

---

### Post by MarkMcLT on 2009-12-14
Ok, I found a couple of resources online that suggested that the Gnome network manager might be responsible for restarting dhclient, so I went in to the gui and entered the same static IP info I had put in /etc/network/interfaces. Then I killed dhclient, and this time it did not come back up. So my hope is that this has fixed the problem.

---

### Post by chili555 on 2009-12-14
Of course, you can always simply remove Network Manager and your worries will go away forever!

---

