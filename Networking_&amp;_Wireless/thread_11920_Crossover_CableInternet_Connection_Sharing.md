---
title: "Crossover Cable/Internet Connection Sharing"
date: 2005-01-20
forum: Networking &amp; Wireless
---

### Post by new2linux on 2005-01-20
Hi,

    I have an xp computer set up to share its internet connection.  I then plugged a crossover cable into its network card.  When I plugged the other end of the cable into a 98 box it worked great.  However, when I plugged the end into a ubuntu box, the internet doesn't work.  

   Is there a way that I can get my ubuntu box to access the internet over the crossover cable?

EHD

---

### Post by new2linux on 2005-01-20
Would it help if I hooked up the cable and then re-installed ubuntu?

---

### Post by stoffe on 2005-01-20
Well, make sure you use DHCP, see "man interfaces" and the file "/etc/network/interfaces" (there is probably some good tool for this too, but I'm new to Ubuntu and Gnome). If that isn't enabled now, and you do, all you would have to do is restart the network, I think the easiest way is via "sudo /etc/init.d/networking restart", but a common reboot would also work. ;)

As far as I can remember, that is all there is to it, enable DHCP.

---

