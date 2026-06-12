---
title: "How do I make my router forward a signal?"
date: 2009-05-15
forum: Networking &amp; Wireless
---

### Post by Fzang on 2009-05-15
I have a main internet/everything box from the ISP that's connected directly to the internet. This box can broadcast wirelessly, however, it's not powerful enough to reach a computer in the other end of the house

I also have a netgear router which can broadcast a signal that's strong enough to be used by the far-away computer

Now, how do I make the netgear "forward" the signal from the box? I wired up the netgear to the box but it doesn't have internet access.

I believe I have to mess with netgear's settings to make it forward another signal, but I have no idea what I have to click

Help please..

---

### Post by freebeer on 2009-05-15
It would probably help if you posted up the modem make and model number, and that of the netgear router, too.

I'm guessing at this point you don't have the netgear's gateway address set to that of your modem.  You might also have to ensure that the hardware is all on the same subnet.

---

### Post by Fzang on 2009-05-16
I've taken screenies of nearly every config page of the 2 routers

The TDC pictures are for my modem/box/wireless thing

Uploaded here:
[http://www.mediafire.com/download.php?u4yqm4dgd3n](http://www.mediafire.com/download.php?u4yqm4dgd3n)

Despite what the pictures may inform you of my heretics, I also have 9.04 installed :p

---

### Post by freebeer on 2009-05-16
Ok, I've never tried to hook up a router behind another router (in your case a router/modem combination).  So I don't have a direct solution for you, but perhaps I can show you where to concentrate your efforts.

It looks like your netgear router and your router/modem have the same internal (LAN) IP address.  That's where your conflict is.  You can see this in pictures tdc1.png and net3.png.  I suspect that if you give the netgear an internal IP address of, say, 192.168.100 and a gateway address of 192.168.1.1, traffic going through the netgear now has a path to the router/modem and out to the internet.  You'll want to make sure that the netgear router (if you continue to allow it to provide IP addresses to machines connected to it) provides LAN IP addresses in the range 192.168.1.101 to, say 192.168.1.150.  The TDCI router would provide addresses from 192.168.1.2 to 192.168.1.99.  This way the TDCI router provides the IP addresses and direct traffic to the machines directly connected to it.  Otherwise it passes traffic intended for machines connected to the netgear router to 192.168.1.100 which, in turn, passes traffic to the correct machine.  That's a little tricky to describe, so maybe a picture will help.  Sorry, it's a rush job and I don't do graphics well.  But I hope it gets you a little closer to what you're trying to achieve.

---

### Post by Fzang on 2009-05-17
Thanks for the help

Anyways, it showed up that my brother couldn't connect his computer BECAUSE HE WROTE THE WRONG PASSWORD!... and I took all the sh**

Thanks anyways

---

