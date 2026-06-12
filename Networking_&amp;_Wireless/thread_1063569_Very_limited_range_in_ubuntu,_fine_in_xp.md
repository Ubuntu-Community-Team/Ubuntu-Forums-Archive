---
title: "Very limited range in ubuntu, fine in xp"
date: 2009-02-08
forum: Networking &amp; Wireless
---

### Post by docjones2 on 2009-02-08
I have a laptop that has two partitions, one windows xp and one Ubuntu.

I have been using primarily the Ubuntu partition for months now without any problem.  Wireless internet was WPA2.

Last night I had to change the encryption to WPA for a different user in my house, long story, but now my Ubuntu partition will only connect to it if I am sitting next to the router.

The nm-applet on my desktop reports that the connection strength is 90% from any location in my house.  When I am connected (when I'm sitting next to the router) I can access the internet, my router has a browser accessible system page, like many routers, and it allows me to monitor current wireless connections and it shows a signal strength percentage.  Whenever connected on my ubuntu partition, it shows 10% despite the fact that I am sitting next to it and that the nm-applet says 90%.

Sitting in the same location using the same laptop on my windows partition, the router says my strength is 69%.  The problem lies somewhere on the Ubuntu partition.  Are there known issues with WPA1 in Ubuntu or any Ubuntu drivers?  There was absolutely no problem when the router was WPA2.

Any help would be much appreciated.  I've grown quite accustomed to the Linux environment.  Linux at my school Linux at my work Linux at my home, I've been groovin' on the Linux every which computer I use, and using windows xp again, simply is not an option, and especially not over something so silly as this.

Thank you.

---

### Post by ForMar on 2009-02-08
The main cause of your problem has to do with drivers, specifically the drivers you are using for wireless. There are some issues that linux has when it comes to the type of encryption that you are using. It really has everything to do with how you installed your drivers and what apps (if any) you used to configure the wireless card. Knowing what card you have might make it easer to tell exactly what your problem is but it might be quicker to just do a little trial and error yourself. Meaning try different drivers that are offered and different programs such as ndiswrapper. GL

---

### Post by docjones2 on 2009-02-09
The problem somehow resolved itself

I have no idea, it miraculously connected tonight after days of refusing to.

Well, thank you for your help

---

