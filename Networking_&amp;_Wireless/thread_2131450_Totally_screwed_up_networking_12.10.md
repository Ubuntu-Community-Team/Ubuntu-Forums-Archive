---
title: "Totally screwed up networking 12.10"
date: 2013-04-01
forum: Networking &amp; Wireless
---

### Post by bmcclint on 2013-04-01
OK…So I guess I like the old days of ethX.  Some of you may know what happened from there.
 
Anayway…I have a Ubuntu 12.10 server built so I’d like to recover if at all possible.  I had one NIC in the system and it was named P4P1.  So OK whatever.  I had to add a dual port NIC for more connections, long story, and they had names P1P1 and P2P1.  I’m a little old school and this is my first Ubuntu build, I’m coming from FC12.  Anyway I wanted to get the old ethX names back.  I read a forum post about removing biosdevnames.  So I removed that package.  Have not seen the network since.  Occasionally I will see after 5-10 minutes the wired connections come up but a reboot loses everything.
 
Am I screwed?  Do I need to rebuild?  I hope not as very little has gone smoothly.  I’ve tired reinstalling biosdevnames again hoping it would just recover, one of those times the wired connection came up with no luck.
 
Suggestions on getting back to biosdevnames or back to the traditional ethX names.
 
Thanks

---

### Post by bmcclint on 2013-04-01
Well...I am attempting to get biosdevname reinstalled.  I have the package installed and any scripts I edited back to normal, etc/networking/interfaces; etc/minidlns.conf and /etc/samba/smb.conf.

When I execute biosdevname -d it shows me all of my devices and the names they would get.  That all looks good.  I simply have no interface up.  I can see the onboard with the cable blinking like its trying to configure but no link light is steady.

On boot is says waiting for network configuration.  It waits for a while then I get try for another 60 secs then it goes to the desktop.

I'm stumped.  Do I need to edit /lib/udev/rules.d/71-biosdevname....?

---

### Post by cariboo on 2013-04-02
Moved to Networking & Wireless, as it really isn't a server problem.

---

### Post by bmcclint on 2013-04-02
NOT solved but working...

ipconfig -a show all three NIC as ethX where X = 0, 1, 2
biosdevname -d show all the NEW names it would like to give as PXP1 where X = 1, 2, 4

Network would not start on reboot.  It would wait for network configuration and another 60 secobnds then dump to login screen.

Manually 'sudo start network-manager' brought up the interfaces with ethX.

Changed /etc/network/interfaces to eth2, my primary, and rebooted.  Everything came up as expected but using old ethX names which is what I was trying to get to.

Questions...biosdevname is installed and see names but not doing anything.  Uh?  Should I be concerned?  Is my install tainted?  Should I uninstall biosdevname?  Will I end up back in a work of hurt?

I'm kind of getting to a point where if it aint broke don't fix it but is it broke?

Any insight is grealty appreciated...

---

### Post by Iowan on 2013-04-02
Just my opinion:
If it works - ESPECIALLY if it works (more or less) the way you wanted - I'd be inclined to leave it.

---

