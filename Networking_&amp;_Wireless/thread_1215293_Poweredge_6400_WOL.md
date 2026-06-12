---
title: "Poweredge 6400 WOL"
date: 2009-07-17
forum: Networking &amp; Wireless
---

### Post by mybluevan on 2009-07-17
Ok, I've looked through the forums for a couple hours now and can't seem to find anything helpful dealing with this specific problem. I have a Dell Poweredge 6400 with an Intel Pro 100 NIC build onto the MB using the e100 driver. I'm running Ubuntu 9.04 Server. I checked the Dell documentation and it said that I basically had to 2 options for WOL.

1. Cold boot, as in disconnect the AC for 30 sec. and plug it back in.
2. WOL configured through the OS, i.e. "ethtool -s eth0 wol g"

The first method works fine, so I know the hardware is working right and configured. The second method says to run "ethtool -s eth0 wol g", "halt" the system, the NIC should stay on, and a MagicPacket should boot the system. I also looked at the WOL guide in the forums for information and this is the final method I came up with:

1. Write a script or manually run "ethtool -s eth0 wol g" after each boot. I confirmed with "ethtool eth0" that the WOL mode is successfully being set to "g".
2. Edit /etc/init.d/halt to set "NETDOWN=no" (I tried this with both "yes" and "no")
3. I tried using the GUI shut down and calling halt from the command line.
4. Regardless of what I tried in steps 1-3 the NIC light turns off just before the main system power dies.
5. MagicPacket receives no response.

As I mentioned before, the MagicPacket works fine after the AC is cut, so I know the hardware is operational. Therefore it seems the issue is somewhere in the halt process. Something is killing the power to the NIC just at the end of the power down regardless of the WOL setting.

I do a lot of remote work on my servers and the 6400 sucks so much juice that I can't leave it on all the time. I would GREATLY appreciate any help or suggestions you might have.

---

### Post by koszta on 2010-02-22
I got it solved, I very much suspect you having the very same issue as I do. It is a driver problem (proprietary drivers needed) - you can find a solution in this thread. [http://ubuntuforums.org/showthread.php?t=1410101](http://ubuntuforums.org/showthread.php?t=1410101)

if you still care :)

---

### Post by mybluevan on 2010-02-22
Thanks for the tip, looks like I may have to upgrade to Karmic and get the 2.6.31-14 kernel though.

---

