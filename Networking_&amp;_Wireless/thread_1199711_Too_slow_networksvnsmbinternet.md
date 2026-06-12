---
title: "Too slow network/svn/smb/internet"
date: 2009-06-29
forum: Networking &amp; Wireless
---

### Post by tarekeldeeb on 2009-06-29
Hello all, 

I have a lab:
1 server : Fedora with internet sharing, SVN server, Samba server
Many clients: (some windows,  some ubuntu)

The ubuntu PCs where built using a custom remastersys live cds
Everything went fine for months ..

Then I updated this custom live CD using remastersys, just as done before. I just updated the packages .. removed some unneeded, add some extra tools. Then got my newLive.iso

Some old windows PC where converted to ubuntu using the newLive.iso

Those PCs now have too slow internet connections ( much less than 1  kbps) many sites do not load .. many get disconnected while loading ..

SVN check-out from the server is not possible .. connection is reset by peer!

Even the samba shares .. too slow .. nothing may be copied from the server ..


I really did not face such problem before ..

Meanwhile .. the other windows PCs work great .. the old installed ubuntu also work great ..

So the newLive.iso has some problems .. 

What could be the problem? Any clues?

I checked the MTU for the network interfaces >> 1500 .. good.
I do not know hat else to check :(

Please , I need urgent help.

---

### Post by tarekeldeeb on 2009-06-29
oooh !

The fedora dhcp server is giving the PCs duplicate IP!!
I changed the ip range in the /etc/dhcpd.conf and still duplicates occur .. in the PCs with the newLive.iso

doesn't the dhcp server distinguish the clients with their MAC address? Is this related to the installed ubuntu image?

---

### Post by tarekeldeeb on 2009-06-29
ifconfig showed different PCs having the same MAC !!

how can this be fixed?

---

### Post by dmizer on 2009-06-30
Found this with a workaround posted: [http://ubuntuforums.org/showthread.php?t=379520](http://ubuntuforums.org/showthread.php?t=379520)

There is also some further discussion without definite resolution.

---

