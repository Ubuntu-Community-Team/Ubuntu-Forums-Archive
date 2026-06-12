---
title: "Mythbuntu Backend Static IP"
date: 2016-04-24
forum: Mythbuntu
---

### Post by jlp_engineer on 2016-04-24
I decided one day to change the IP of my backend since I also decided to change the subnet addressing on my local network.  The decision to do this was a long time in the making, and planned carefully.  I loaded up a new PC with firewall software, and began to plan out the new network.  Once everything was ready I pulled the plug on the old firewall, and plugged in the new one.  I then rebooted all my DHCP devices on the network, after reserving a portion of the /24 network for static IP devices in my network.  After some initial disappointment with my HDHR, since I could not set a fixed IP on the device, I started to have issues with my Mythbuntu backend, which was still running on the old network scheme.  So I changed the IP of the server using the GUI tool, and then checked the IP in a terminal window, and it was still set to the old IP.  I then rebooted, and was all good.  I then changed the IP on Mybuntu Backend setup, but none of my Frontends were able to connect.  Checking the logs gave me mixed results and no clear idea what was wrong.  

After hours of trying things, I decided to put my network back to the way it was, since the family wanted the TV's in the house to start working again.  Then to my horror, that didn't work either.  Then I remembered having to reset the MySQL network access back to "Enable" once after messing with some other part of the setup, and sure enough, it was disabled,  After correcting that, all was good.  Once I was able to reflect on it, my guess was that this was my issue when I went to change the IP in the first place.

So my question is this: Once you change the server IP, or the IP in Mybuntu backend setup, should the MySQL network access automatically disable itself?  Is this a "feature"? :confused:

So steps to changing the fixed IP on a Mybuntu backend server:

1 - Change the IP of the system and reboot.

2 - Change the IP in Mythbuntu backend setup (two places on the same screen).

3 - Re-enable network access for MySQL using Mythbuntu Control Center.

I think the file where most of these settings are is the config.xml file, but does anyone have an example of what it should look like on a backend that is ONLY accessed remotely by frontend on the same network subnet?  For example, I think localhost should be replaced by an IP, or is that not correct?

Thanks for any and all information.

---

### Post by aelfric55 on 2016-04-26
> So my question is this: Once you change the server IP, or the IP in  Mybuntu backend setup, should the MySQL network access automatically  disable itself?  Is this a "feature"?

A network-accessible mysql server doing TCPIP on a static IP normally has the service bound to that IP with a "bind" statement in the my.cnf file under /etc. If the IP address on the machine changes, the address in the "bind" statement also needs to be changed (and the service restarted) in order to enable the mysql service on the new IP. 

So to the extent that this edit may be done for you from a utility like the MCC, then yes, I suppose it's a feature.

---

