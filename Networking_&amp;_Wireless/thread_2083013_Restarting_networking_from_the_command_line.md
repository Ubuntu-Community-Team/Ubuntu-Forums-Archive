---
title: "Restarting networking from the command line?"
date: 2012-11-11
forum: Networking &amp; Wireless
---

### Post by AussieGuy on 2012-11-11
Recently I've been having a few network problems at home.  They can usually be fixed by rebooting the modem/router, and then (if necessary) restarting the networking system on my laptop.  This is where things get tricky.  I'm running Ubuntu 12.04 LTS, and 

"sudo /etc/init.d/networking stop"

does seem to stop networking.  But then:

"sudo /etc/init.d/networking start"

returns a message telling me to use start(8).  But:

"sudo service networking start"

returns "networking stop/waiting"

as does 

"sudo start networking"

I tried to use the Networking menu in my KDE System Settings application, but clicking on "Networking" caused System Settings to crash with a seg fault.  I ended up rebooting (which is how I'm online now).

I'm quite confused about upstart, so to the question I posed in the title - how can I manage networking from the command line? I mean stopping and restarting the networking system, and then restarting wireless (I would normally just do "sudo ifconfig wlan0 up"), but maybe that's wrong too.

Any advice, or pointers to web pages would be very helpful!

Thanks,
-A.

---

### Post by ajgreeny on 2012-11-11
Try ```
ifconfig
``` which may show your connection name ie eth0 or eth1, then try ```
sudo ifconfig eth0 up
``` using the eth# that ifconfig gave you.

If the ifconfig command alone does not show an address, but just the "lo" output, right click on the network icon in your panel and make sure that "Enable networking" is selected.

---

