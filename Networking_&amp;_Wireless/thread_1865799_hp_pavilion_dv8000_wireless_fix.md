---
title: "hp pavilion dv8000 wireless fix"
date: 2011-10-20
forum: Networking &amp; Wireless
---

### Post by gride on 2011-10-20
so i tried a few of the solutions here and this is what i found that worked for me

> I am  going to install the correct driver for this wireless card.  Then I will remove the &#8220;incorrect&#8221; driver (bcmwl) which Ubuntu installed  by default.

 sudo apt-get update 
sudo apt-get install firmware-b43-installer 
sudo apt-get remove bcmwl-kernel-source 
sudo reboot 



i found it at this website link;
[http://nfolamp.wordpress.com/2011/10/15/ubuntu-11-10-getting-wireless-bcm4311-working/](http://nfolamp.wordpress.com/2011/10/15/ubuntu-11-10-getting-wireless-bcm4311-working/)

thanks neil=)



and also.
 im new to still fairly new to ubuntu. i switched to gnome3 and loving it
unity was buggy for me

---

