---
title: "can't boot after installing nw script on /etc/rc2.d"
date: 2006-03-12
forum: Networking &amp; Wireless
---

### Post by melquiades on 2006-03-12
guys,
        I've been working on getting my wifi running on ubuntu. I have a RaLink wifi card ( rt61 ), and after following the howtos I've been successful iin getting my wifi up and running in ubuntu. I tried rebooting to see whether the changes would remain persistent after shutdown. As expected, the driver was automatically loaded during bootup. The only snag was that the wifi device 'ra0' had to manually configured and activated after bootup. so I followed the final instruction in the howto and saved a script on /etc/init.d and made a link on /etc/rc2.d. here's the short script.

#!/bin/sh
echo "Bringing up ra0"
# obtain an IP address from a DHCP server
dhclient ra0

# alternately, you can uncomment the following line to set a static IP address
# ifconfig ra0 {IP ADDRESS} up
# if you uncomment the line above, make sure to comment line #4

i followed the howtos recommendation and saved the script as rt61up on /etc/init.d. I'm not so sure if I recall right but on the /etc/rc2.d i named the link S15rt61 and pointed it on rt61up. After that, I restarted and things haven't been right since. The bootup process hangs during the 'Configuring network interfaces' part. I tried the recovery mode but still ubuntu won't boot right. Please help, this is way too complicated for a newbie like me.

Thanks in advance,
melquiades

---

### Post by bscbrit on 2006-03-12
OK, before I can help you fix the problem, I need to know what mode you can boot your machine into.  When you boot into recovery mode, do you eventually get to a commandline?  (Recovery mode does not run under a GUI - it might be the GUI that you are trying to fix :D )

---

### Post by melquiades on 2006-03-12
I don't get to see a commandline during recovery mode, since it freezes during the bootup process, i can't remember exactly during which phase of the bootup.

---

### Post by bscbrit on 2006-03-13
Then I suspect that you have changed more than you thought.  If you boot the machine (and leave it alone for, say, 10 minutes) it should eventually ignore the network and arrive at either the command line or GUI logon.  If it doesn't get even that far then you have changed more than the network configuration.  When it freezes, what is displayed on the screen? i.e. what is it stuck doing? (Yes, I know you said configuring network interfaces, but that should time out if I remember correctly)

---

