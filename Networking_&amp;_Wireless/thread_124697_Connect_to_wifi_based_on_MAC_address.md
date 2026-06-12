---
title: "Connect to wifi based on MAC address"
date: 2006-02-02
forum: Networking &amp; Wireless
---

### Post by nickj6282 on 2006-02-02
Good evening list,

I have a Netgear router that my girlfriend gave me, and I'm trying to connect to it wirelessly so I can change it's settings. The problem is that another person in my apartment building has a Netgear router with the default SSID (NETGEAR), so when I try to connect I end up on their network every time. I can't seem to connect with an ethernet cable, because whenever I plug one in to any switch, my computer crashes! So I'm stuck doing this wirelessly until I have time to figure out my crashing problem. I'm getting fairly frustrated and I'm about ready to do something evil (like change the SSID of my neighbor's router and set it to encrypted so my PCs stop connecting to it)

Thanks
-Nick

---

### Post by hajk on 2006-02-02
Try and use a live CD, like the Ubuntu live-CD or Knoppix, in connection with an Ethernet cable to change the settings in your router. If all else fails, you could also try and do the same from Windows...

---

### Post by davinci on 2006-02-02
try this:

man iwconfig

> 

       ap     Force the card to register to the Access Point given by the address, if it is possible. When the quality  of  the  connection
              goes too low, the driver may revert back to automatic mode (the card selects the best Access Point in range).
              You  may  also  use  off to re-enable automatic mode without changing the current Access Point, or you may use any or auto to
              force the card to reassociate with the currently best Access Point.
              Example :
                   iwconfig eth0 ap 00:60:1D:01:23:45
                   iwconfig eth0 ap any
                   iwconfig eth0 ap off


---

