---
title: "Constant drops in wireless connection"
date: 2009-12-02
forum: Networking &amp; Wireless
---

### Post by solwic on 2009-12-02
I have a Linksys WMP54G wireless PCI card that I use to connect to the Internet.  In Ubuntu, I get dropped multiple times a day (usually more than a dozen, and usually in bursts of 5 or more).  My connection will disconnect, then try to reconnect.  Sometimes it manages to reconnect, usually it doesn't.  Those times I have to go back into the settings and re-enter my wireless password to gain access.  

In an effort to narrow down the problem, I booted up Windows XP on the same machine (I dual boot), installed the drivers from Linksys, and let Windows manage my connection.  I got dropped far less often (usually no more than 2 or 3 times a day), but was still getting dropped.

Then I let the Linksys "Wireless Network Monitor" handle my connection, rather than Windows XP's program, and today is day 3 with no drops at all.  

Not only that, but in Ubuntu my download speed was 100k max.  With Windows wireless manager, I got up to 250k.  Now with the Linksys manager I'm pulling my full line speed, ~900kbps.   

My question is this:  how can I get this card to work in Ubuntu?  Ubuntu recognizes the card out of the box and installs drivers that work (as described above) partially, but when I use ndisgtk to install the Linksys driver, it says it's an invalid driver.  I know it isn't, because they work perfectly in Windows.  (And yes, I know to use the .inf file as the driver).  

Am I missing something?  I mean, it's kind of nice to have Windows back, and it's nearly as quick as Ubuntu is on this machine...but I miss Ubuntu, and would really love to have a steady connection in Linux.  There's just something about Windows that makes me feel dirty....  :P

Any ideas would be greatly appreciated.  Do I have to blacklist the generic driver in Ubuntu before I can install the Linksys driver (which is something I've never had to do before on any other computer).

Also, I'm sure this isn't a router issue.  Like I said, it's working perfectly now that I'm using Linksys's program, and my brother's Acer laptop runs Ubuntu 9.04 perfectly, with only one drop/reconnect after boot (which is normal; it's always done that).

Thanks!

EDIT:  If it matters, I'm running Ubuntu 9.04 on a 2.0Ghz CPU, 1.5GB RAM.

---

### Post by solwic on 2009-12-03
Nobody has any ideas?  Does anybody know if Linux Mint has a different network manager than Ubuntu?

---

### Post by clev_browns_fan on 2010-03-27
Did you ever find a resolution to your problem?  I am having the same issue.

---

### Post by clev_browns_fan on 2010-06-04
Solution:  Upgraded to Ubuntu 10.04 DTS.:guitar:

---

