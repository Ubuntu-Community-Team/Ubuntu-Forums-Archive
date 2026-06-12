---
title: "attaching switch to router disables wireless"
date: 2009-12-23
forum: Networking &amp; Wireless
---

### Post by gamblor01 on 2009-12-23
Hi all,

I have a wireless router with a 4-port switch built in.  The router is a Linksys WRT310N.   I have more than 4 devices that I would like to connect through wired connections...so I have an 8 port switch that I connect into one of the 4 ports on the back of the router.  Whenever I do this, the wireless functionality stops working!  To get wireless back, I just have to unplug the gigabit switch (and unplug/plug in the router) and wireless is back up and running.

It doesn't seem to matter which port I plug the switch into so that isn't the cause of this.  Also, I can connect up 4 devices where none of them is a switch (i.e. 4 computers) and wireless still works just fine -- so it doesn't seem to be a problem that there are 4 devices attached.

What am I missing here?  Connecting the gigabit switch keeps killing my wireless.

Oh and I should mention, when the switch is connected to my router, the devices behind it work just fine.  However, the wireless devices all obtain 169.254.*.* addresses so clearly the clients are failing to obtain an address from the router (the DHCP server).

---

### Post by Iowan on 2009-12-24
First I thought maybe the router's DHCP server was only set for 4 leases, but that shouldn't kill wireless until router is rebooted. Is it just that switch? Does it lock up wireless if no devices are attached to the switch?

---

### Post by gamblor01 on 2009-12-24
So I posted this on another forum, and someone asked if my switch was acting as a DHCP server too.  I didn't think they could, but anyway things are working now.  Here is my response....



OK...weird. I spent hours yesterday trying to figure this out and then went to bed. I wake up this morning and wireless works -- even with the switch attached. EVERYTHING WORKS!!! I almost want to power cycle my router to see if the same nonsense happens again but I'm scared to at the moment (let me finish my work day first).


I didn't think that switches could be DHCP servers...

It's a Netgear GS108:

[http://www.netgear.com/Products/Swit...hes/GS108.aspx]("http://www.netgear.com/Products/Switches/DesktopSwitches/GS108.aspx")

In any case I don't believe that it is acting as a DHCP server. The systems behind it (all wired) get an IP address assigned to them. I also noticed some other strange behavior. I have several MAC addresses that I automatically assign reserved IP addresses. So one computer has 192.168.0.2, another has 192.168.0.3, two laptops have 192.168.0.4 and .5, and then my VOIP systems gets 192.168.0.6.

Last night when I had the switch plugged in, I certainly didn't expect any of the wireless clients to show up, but when I checked my DHCP client table, I would ONLY see the .2 and .6 addresses in the table. Oddly enough, my second computer WAS connected through a wired connection and had an address (192.168.0.3). ifconfig showed that it had the address, and I could certainly use it, ping other boxes, etc.

So for some strange reason that system didn't show up in the DHCP client table in router's config page. Also, none of the systems attached to switch showed up there either.


Now all clients show up properly in the table, wireless works, and everything as expected. I don't know what the heck happened (though it would be nice to know in case it happens again in the future, or the power goes out or something). I'm happy it's working though!

---

### Post by gamblor01 on 2009-12-24
Ok I lied...this problem is not yet solved.  Iowan it looks like you were on to something.

The wireless clients ONLY work when the systems attached to the gigabit switch are OFF. If there is any traffic from a system attached to that switch, then the wireless just stops working. As soon as I turn off those devices attached to the switch, wireless fires right back up.


The router allows for leases of up to 100 clients.  I think max I have 8 systems connected (a mix of wired and wireless clients).  What on earth is happening here?

---

### Post by gamblor01 on 2009-12-24
Well nevermind. I was able to reconfigure my network in such a way that the 8 port switch is no longer necessary. I do not intend on continuing the troubleshooting for this, as I don't want to break everything again. I still do not believe that connecting a switch should disable my wireless though. I was either missing something or there is a defect somewhere.

---

### Post by Iowan on 2009-12-24
For what it's worth:
I don't understand it either... nor do I blame you for leaving a working (reconfigured) system alone.
Ordinarily, I'd suggest marking the thread [SOLVED], but it isn't - so maybe an answer will show up sometime.

---

