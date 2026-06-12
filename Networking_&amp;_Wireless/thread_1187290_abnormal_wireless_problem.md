---
title: "abnormal wireless problem"
date: 2009-06-14
forum: Networking &amp; Wireless
---

### Post by texturednb on 2009-06-14
I'm experiencing an odd problem with a netgear wg111v3 usb nic, no big surprise there.I'm attempting to run 64 bit 9.04 ( i think) ubuntu the most recent 64 bit stable build i have followed a portion of the wireless trouble shooting tips but wanted to check everyones experiences before i go modding code because this is a little atypical. ubuntu automatically loads a default driver that allows it to detect my network properly and even connect or at least say it is connected it even recieves an IP and appears to have the correct DNS it just doesn't seem to receive any usable packets. Sort of feels like an IPv6 issue nut i'm not sure and cant alter code without eiyher a HDD install or recompile i think (i'm relativrly new to commandline and code) or is this a problem with the driver not properly interpreting the nic output?  any insight would be appreciated

---

### Post by superprash2003 on 2009-06-15
it depends.. are you able to ping machines in your LAN or internet perfectly?

---

### Post by texturednb on 2009-06-16
hope i didn't miss my window of oppurtunity was away for a day.can't ping windows machines can ping router and google.Can load most of a search page but loading hangs and then stalls completely google search results will usually load all the way but any full page wil not load.This is after switching to 32 bit appearantly  there is no wireless support for 64 bit anything and this card. I have since read on this forum that this card has an issue with 1Mbps transfer speed cap and a 200KB total cap i believe that this is what i'm up against a brick wall but if you have any suggestions i will be glad to attempt them

---

### Post by superprash2003 on 2009-06-16
you could try 2 things
1)use opendns servers - 208.67.222.222 and 208.67.220.220 [http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html)
2)change MTU value - [http://www.prash-babu.com/2009/06/how-to-change-mtu-in-ubuntu-using-gui.html](http://www.prash-babu.com/2009/06/how-to-change-mtu-in-ubuntu-using-gui.html)

about the windows machine pinging part , you need to check the firewall..

---

