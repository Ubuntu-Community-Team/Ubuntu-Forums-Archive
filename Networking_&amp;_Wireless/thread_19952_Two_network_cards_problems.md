---
title: "Two network cards problems"
date: 2005-03-14
forum: Networking &amp; Wireless
---

### Post by dcorreal on 2005-03-14
Hi

I'd Installed Ubuntu Warty in my Dell GX270. This machine has an Intel network built-in,  The network works fine.  Now, I have to install a second network card (REaltek 8139) but as soon as I did  the network stops working.  If i deactivated the Realtek card everything is working again.   

The thing is that I need to configure my Ubunut as a gateway in order to share de internet connection.

The intel card has an Public IP and the realtek has 192.168.1.1

What is wrong with my configuration.

Thanks in advance!!!

---

### Post by alastair on 2005-03-14
No idea. Define "not working"? Driver fails to load? No network access? Perhaps it's just a "route" problem.

Check the logs when both are in - make sure no errors on driver load etc.

/var/log/syslog

After both are installed, check :

ifconfig -a

and also routing :

route -n

Do some digging.

---

