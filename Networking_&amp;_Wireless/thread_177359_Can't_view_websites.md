---
title: "Can't view websites"
date: 2006-05-16
forum: Networking &amp; Wireless
---

### Post by mike.evans on 2006-05-16
Hi,

My Ubuntu installation as running fine until yesterday when I booted up I could no longer view web pages, or use FTP. The only thing I can do is ping addresses and view my router config pages. I can't view webpages at all, not through a browser, or wget... it just gets stuck on the connecting stage (but resolving the IP works fine). I haven't changed any config, or even installed anything new for a day or two before this happened. I even tried a re-install and got the same problem.

I'm using a Linksys wireless router (but this machine is wired). I can connect both wired and wireless with my Windows laptop with no problems viewing web pages, and when I boot my desktop in to Windows it all works.

Any ideas what could be causing it?

Thanks,
Mike

---

### Post by mips on 2006-05-16
Try disbaling ipv6 by renaming the module.

---

### Post by mike.evans on 2006-05-16
I've just tried disabling IPv6 using this: [http://www.ubuntuforums.org/archive/index.php/t-6841.html](http://www.ubuntuforums.org/archive/index.php/t-6841.html) but I still have the same problem.

---

### Post by mpvano on 2006-05-16
Sounds like your DNS settings may be clobbered. Do you use wireless anywhere else?

How do you get your network settings? What you describe can happen easily if you are trying to use static addressing on your machine, or if your local router is not configured to provide DNS setting information.

cat /etc/resolv.conf

to see the current DNS setup.

If the DNS is being clobbered by DHCP when you use other wireless networks, The fix is to make sure the DNS gets reset properly when you get home.

If you use DHCP at home, make sure that the router has DNS entries and that they are correct.

If you use static addresses at home, you need to also reset the DNS settings when you switch back to your home setup. How to do that depends on exactly how you go about setting your configuration. In my case, I added a shell command to /etc/network/interfaces that "echoes" to resolv.conf to restore my settings.

You should also check your windows settings and look and see what DNS you are using there. It's possible that the windows settings work, but that your router or linux settings are wrong. They may point to a different nameserver that's no longer available.

Don't forget that in most cases dns settings don't have to agree with your ISP's settings - unless something is filtering your DNS requests and blocking them, you can use ANY server that's part of the DNS system from anywhere on the internet. It's customary to use the ones recommended by your ISP because they're normally much faster to get replies from, and they're more likely to know about "private" servers (Ones that are not publicly visible from the internet).

Another problem that used to happen about a year ago was the installation of "bogus" DNS servers into local machines by trojans. Another machine on your LAN may have been taken over by a trojan. Sometimes these take action to block other DNS servers on your lan from working properly so that the trojan can install it's own DNS server. This sometimes even happens to routers that don't have their configuration security settings locked down properly.  I haven't seen this happen for a few months, but it could be making a resurgence.....

Hope this gives you some ideas about a few things to check.

Mario

---

### Post by mike.evans on 2006-05-16
Thanks for the reply. I'm currently using two computers on my network (1 desktop, and one laptop). Both were working fine until yesterday when I booted up. The thing is, applications resolve IP's fine (so I assume there is no problem with DNS). For example:

#wget google.co.uk
--15;54:50--   [http://google.co.uk](http://google.co.uk)
                => `index.html.1`
Resolving google.co.uk... 216.239.39.104, 216.239.59.104, 216.239.57.104
Connecting to google.co.uk[216.239.39.104]:80

And it gets stuck there. It doesn't seem to be an issue with just port 80 as I have tried FTP and an admin panel that uses port 2222, none of which are working. I can also ping any addresses without error.

I hadn't changed settings of my router or computer any time soon before or after it stopped working. I've tried re-installing Ubuntu, installing Debian... same errors. 

I haven't got a clue...

---

### Post by changlinn on 2006-05-16
is it just on one computer, it is more than likely going to be hardware related if you have reinstalled ubuntu, and installed debian and it still doesn't work.
My suggestion switch the network cable, switch ports on the switch, try a different network card.
If it is both pc's it could be something screwey with your router.

---

### Post by Iowan on 2006-05-16
Check the DNS settings in the router - I've noticed several posts involving DNS issues with Linksys routers (especially if DHCP is involved).

---

### Post by mike.evans on 2006-05-17
changlinn, it is just one computer, but as I said, if I boot in to Windows (its a dual-boot machine) I can connect to websites with out a problem. So it can't be a hardware issue. But I also can't see how it could logically be a router issue either.

Iowan, DNS is the only thing that actually *does* work. It resolves the correct IP addresses fine for any address, and I can ping them. I just can't do anything else.

---

### Post by mips on 2006-05-17
Mike,

What Linksys are you using & firmware version ?
Also please tell us a bit more about your network setup, modem,router,wireless etc. How is everything connected togetger & subnets used on each.

---

### Post by mike.evans on 2006-05-17
Thanks for your help everyone. It seems to be my router causing the problem. Quite how it managed to single out a particular operating system on a particular machine, I don't know. But i've now linked my desktop directly to my internet connection and it works fine. I've installed another network card and a switch to use my desktop as a router.

---

