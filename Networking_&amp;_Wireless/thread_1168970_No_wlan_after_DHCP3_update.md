---
title: "No wlan after DHCP3 update"
date: 2009-05-24
forum: Networking &amp; Wireless
---

### Post by Mantaraya on 2009-05-24
Hi, to start I new with Ubuntu (and Linux).

After installing DHCP3 with apt-get it seem like I have no WLAN0 anymore.

Both WLAN en ETH are removed from my /etc/network/interfaces list.
Bit of history.
I had Hamachi installed wich worked as well. After a reboot I could not connect not Hamachi anymore. With help from some posts it looked lik my route was wrong. Could not edit it to the correct one. Found a post that DHCP3 should fix this.
If i do a ifconfig can't see my wifi either. I do have a usb wifi dongle.
Any help would be apreciated.

Regards.

---

### Post by MediocreHippie on 2009-05-25
i have a similar problem.
 
 
does anyone know how to add the wlan0 back?:(

---

### Post by nsx2000 on 2009-07-14
I have the same issue as well. I have a Dell Latitude D410 laptop with Intel 2200bg wireless. After installing this stupid update today, along with 7 others in the updater list, my wireless connection is gone. It use to show up as eth0:**** with the asterisks being some letter/number combo.

Now eth0 shows up alone with no sub device. I really need to know if someone knows how to fix this as I use my laptop for online schooling and this really blows. I'll give any amount of info needed...

The message logs look like it identifies the Intel 2200 (ipw2200) correctly, it shows up under lsmod, but other then that I am unsure what to do. It has to do with the subdevice, or whatever it it called, that use to be under eth0:????

I have reset my router and rebooted several times just if anyone asks. When I go and edit my wireless settings, I use to get a popup that said "configuring network" or something to that affect and then it would go away. Now after I change the wireless settings it does nothing but give me the changed icon for about 5 seconds but never tells me it configured anything.

Hope that all helps.

---

### Post by nsx2000 on 2009-07-15
After tons of fiddling I found that the network service no longer has access to /proc/net/dev. Trying to stop and then start the networking service leads to an error on each adapter saying /proc/net/dev: Permission denied

Permissions on the folder are 111 root root. Doing research leads me to believe something with grsecurity is screwed up but nowhere can I find a way to fix this. I tried going into the recovery console and giving 777 access just to see if it would do anything and it does not help in any way but probably open up my network files to hackers. I hope someone knows what to do to help those that run into this like myself. I'm pretty much looking at reformatting the laptop.

Lame, twice in a row updates from the update manager has broken my system. Anyone heard of testing across multiple machines/network cards, or am I just that lucky???

---

