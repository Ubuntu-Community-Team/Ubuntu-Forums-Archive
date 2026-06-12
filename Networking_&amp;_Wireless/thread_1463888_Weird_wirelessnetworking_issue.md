---
title: "Weird wireless/networking issue"
date: 2010-04-27
forum: Networking &amp; Wireless
---

### Post by Ayreonic on 2010-04-27
Hi folks,

I got a weird networking issue while trying to use my wireless connection.

I have an Asus 1201N netbook with a fresh copy of Lucid RC installed.
Cable connection is fine and after installing the rtl8192se-dkms driver compiled by Matt Price ([https://launchpad.net/~matt-price/+archive/mattprice]("https://launchpad.net/%7Ematt-price/+archive/mattprice")) my wireless finally finds my network and stays connected.

Now here is the problem: I can successfully browse and ping to my D-link DIR655 but visiting websites is a no go.

I checked in the etc/resolve.conf if my default gateway is there and that the address is correct. It shows the correct address (192.168.0.1).

I can successfully ping 209.85.229.147 ([www.google.com]("http://www.google.com")) on both ip adress and networkname but pinging [www.microsoft.com]("http://www.microsoft.com") fails...

So I'm lost here because I have limited Linux knowledge of where to find all the different configfiles of networksettings.

I used the search but everything that I tried doesn't work.
How come that I don't have these problems when I use my cable while using the same router?

Any help or directions would be appreciated! :)

---

### Post by Iowan on 2010-04-27
[Here]("http://ubuntuforums.org/showthread.php?t=1376506") is a thread that goes through checking MTU - which might be causing problems.

---

### Post by Ayreonic on 2010-04-28
Thanks for the link Iowan!
Looks very promising. I will try this as soon as I get home. :)

Ok still no luck.
I read the complete post about the MTU sizes and did some google to get some better understanding of the MTU setting.

I started with an MTU size of 1492 but it failed, same for the 1472 size.
1464 hover did respond well so I changed this in my wireless settings via the GUI.
I noticed in the ifconfig output that the MTU size still showed 1492 (this is from the automatic setting) so I did a reboot and that finally changed the setting to 1464.

However browsing still ends up with an unresponsive message :(

What else can I troubleshoot to get some more info where the problem resides?

---

### Post by Ayreonic on 2010-04-29
Little bump. :)

---

### Post by Iowan on 2010-04-29
**route -n** (from a terminal) should show the routes - including your gateway. The */etc/resolv.conf* file should contain the address of your DNS. If your gateway also happens to be a nameserver, you're OK.

---

