---
title: "Ubuntu can see the network, so why can't I connect?"
date: 2009-12-18
forum: Networking &amp; Wireless
---

### Post by Gandalf_the_Grey on 2009-12-18
On my freshly installed Karmic Koala setup, the computer can see the network, and I can connect to Windows shares on the computer I'm using now, but I can't use the Internet.  Empathy returns a "Network error", and Synaptic and apt-get don't function due to internet errors.  I had this same problem before, when I installed Jaunty.  Oddly enough, the problem was resolved by launching Pidgin.  When Pidgin was running, Firefox and Chrome worked, I could download packages, and life was good.  But when I tried to use the same solution again, I found that 9.10 doesn't include Pidgin, but rather Empathy.  Empathy does not work the same way Pidgin did to magically resolve the problem.  I still have access to my old install of Karmic, which was upgraded from Jaunty, on another drive. How can I install Pidgin without being able to use apt-get or synaptic?  I can still boot the old install and transfer files from there to the new install.  Better yet, does anyone know what the problem is exactly?

---

### Post by Fire_Chief on 2009-12-18
It sounds like a gateway setting on the new install of Karmic. Double check the IP address configuration and confirm that it is either using DHCP (and getting the right info) or using a static IP address (and you have the correct default gateway configured).

Cheers!

---

### Post by Gandalf_the_Grey on 2009-12-18
I checked, and it is DHCP (Automatic), with the correct IP address.  Fortunately, I was able to execute the copy of Pidgin stored on my old install's drive, getting me that magical solution again that allowed me to use Synaptic to install Pidgin properly.

---

