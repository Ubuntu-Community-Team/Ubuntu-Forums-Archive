---
title: "Problem setting up Connection Sharing"
date: 2010-03-20
forum: Networking &amp; Wireless
---

### Post by Aaal3 on 2010-03-20
This has already been asked, and answered here: [http://ubuntuforums.org/showthread.php?t=1432642](http://ubuntuforums.org/showthread.php?t=1432642) but there is one problem, this requires a window manager, and network-manager.

I am using Ubuntu 9.10 Minimal with no window manager, and i want to recreate the exact effects of the second post in the above thread.

I have one desktop (Ubuntu 9.10 Minimal) with a USB wireless adapter (wlan1) and an ethernet port (eth0). I want my second desktop (also 9.10 Minimal; connected to desktop 1 via ethernet on eth0) to recieve the connection through desktop 1's wireless.

I realize this is rather easy with network-manager, but I am not sure how to go about it through command line.

I have read the help page on sharing connections, but the command-line examples it show do not work for me.

---

### Post by Iowan on 2010-03-20
I presume [this]("https://help.ubuntu.com/community/Internet/ConnectionSharing") is the help page you referenced - what part isn't working?

---

### Post by Aaal3 on 2010-03-20
> **Iowan said:**
> I presume [this]("https://help.ubuntu.com/community/Internet/ConnectionSharing") is the help page you referenced - what part isn't working?
Yes, that is the page i was referencing.

My problem is that i follow all of the directions, and my second desktop still doesn't recieve any connection. After typing the commands, I typed dhclient on the second desktop, and it got "No DHCPOFFERS recieved. No working leases in persisten database - sleeping".

I'm not quite sure what the problem is. I may have messed up on the commands, as it doesn't really explain what parts I should change.

If those instructions do not forward from wlan1 to eth0, then it obviously wouldn't work I guess.

---

### Post by Iowan on 2010-03-20
Are you using a crossover cable between the two machines? (Some gigabit NICs will autoconfigure, but most computer-computer connections need crossover cable) A switch/hub/router between the tow would use straight cables.

---

### Post by Aaal3 on 2010-03-20
> **Iowan said:**
> Are you using a crossover cable between the two machines? (Some gigabit NICs will autoconfigure, but most computer-computer connections need crossover cable) A switch/hub/router between the tow would use straight cables.
Sorry you lost me just a bit there :o. I believe the problem is that the directions of that page are not specifically telling how to do from wlan1->eth0, i believe it is eth1->eth0(?). If you could help me rewrite those commands to go from wlan1->eth0 that would be great :).

---

### Post by Iowan on 2010-03-20
> **Aaal3 said:**
> Sorry you lost me just a bit thereSorry...
There are a few similar threads around. At the bottom of the referenced help page is a link for wireless, but it, too, is the wrong way around. 
Before the wlan1-eth0 comes into play, the client machine will need to connect to the "server". The proper cable will be required for that to happen. Next, it will need an IP address. If DHCP won't play, you can probably configure a static address - but first things first...

---

### Post by Aaal3 on 2010-03-20
> **Iowan said:**
> Sorry...
There are a few similar threads around. At the bottom of the referenced help page is a link for wireless, but it, too, is the wrong way around. 
Before the wlan1-eth0 comes into play, the client machine will need to connect to the "server". The proper cable will be required for that to happen. Next, it will need an IP address. If DHCP won't play, you can probably configure a static address - but first things first...
Ok , I see. So what now?

---

### Post by Iowan on 2010-03-20
(Should probably be using IRC - but this works too...)
Are you using a crossover cable between the two machines?
I've (hopefully) attached a .jpg of a crossover cable. A straight cable would have the same color code on both ends. You could hack up a straight cable - *might* work short distance for awhile...

[Another]("http://www.wlanbook.com/ethernet-crossover-cable-pinout/") pinout that only switches orange and green wires.

---

### Post by Aaal3 on 2010-03-20
> **Iowan said:**
> (Should probably be using IRC - but this works too...)
Are you using a crossover cable between the two machines?
I've (hopefully) attached a .jpg of a crossover cable. A straight cable would have the same color code on both ends. You could hack up a straight cable - *might* work short distance for awhile...
Ill contact you on IRC.

---

### Post by Iowan on 2010-03-20
> **Aaal3 said:**
> If those instructions do not forward from wlan1 to eth0, then it obviously wouldn't work I guess.
The [NAT]("https://help.ubuntu.com/community/Internet/ConnectionSharing#Configure%20NAT") configuration will need to be changed to use wlan1 instead of eth0

---

