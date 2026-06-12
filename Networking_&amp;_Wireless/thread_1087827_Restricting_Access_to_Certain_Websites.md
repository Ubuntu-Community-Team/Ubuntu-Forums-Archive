---
title: "Restricting Access to Certain Websites"
date: 2009-03-05
forum: Networking &amp; Wireless
---

### Post by andriy.kostyuk on 2009-03-05
I would like to restrict the time my children spend playing games in Internet and see the URL of the sites they access. 

What is the most convenient software for this purpose?


(I have Ubuntu 8.10 on a desktop. I have the administrator privileges, my children do not. )

Thank you in advance.

---

### Post by xpod on 2009-03-05
You could use [Opendns](http://www.opendns.com/).It has a content filtering solution you can use....plus your browsing may well feel that bit snappier into the bargain.
You dont have to install anything,just set your computer(or router) to use the OpenDNS servers rather than your ISP`s.It`s all explained on the site.

Either that or your [hosts file](http://howto-ubuntu.com/2008/11/26/blocking-websites-using-the-hosts-file/)

---

### Post by andriy.kostyuk on 2009-03-05
> **xpod said:**
> You could use [Opendns](http://www.opendns.com/).It has a content filtering solution you can use....plus your browsing may well feel that bit snappier into the bargain.
You dont have to install anything,just set your computer(or router) to use the OpenDNS servers rather than your ISP`s.It`s all explained on the site.

Either that or your [hosts file](http://howto-ubuntu.com/2008/11/26/blocking-websites-using-the-hosts-file/)

Thank you!

One more questions.

How can I see the list of sites that were accessed by my kids during, say, last week?
Is there any log file?

---

### Post by xpod on 2009-03-05
> How can I see the list of sites that were accessed by my kids during, say, last week?
Is there any log file?

You can view their browsing history through the browser.
If their using Firefox just check History>Show all history up on the menu bar.
Obviously they can easily delete that if they want.;)

---

### Post by andriy.kostyuk on 2009-03-05
> **xpod said:**
> You can view their browsing history through the browser.
If their using Firefox just check History>Show all history up on the menu bar.
Obviously they can easily delete that if they want.;)
Does not any logfile exist? Or cannot I setup logging of the accessed websites?

---

### Post by xpod on 2009-03-05
> Does not any logfile exist? Or cannot I setup logging of the accessed websites? 

I guess you`ll need to go read up on iptables logging & such but i have a better idea.......just ask them;)

---

