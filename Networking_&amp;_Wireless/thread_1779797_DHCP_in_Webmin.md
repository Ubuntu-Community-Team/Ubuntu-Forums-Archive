---
title: "DHCP in Webmin"
date: 2011-06-11
forum: Networking &amp; Wireless
---

### Post by cstone1983 on 2011-06-11
I am starting to pull out my hair...the dhcp server will not show up on my webmin servers tab. I have it installed "dhcp3-server" but it wont show up in the list so i cant do anything with it. I have tried removing it and having webmin install it but it wont show up still. It does install fine. it says "The DHCP server /usr/sbin/dhcp3 could not be found on the system" it dose give me the option to update the config file. Have they moved the directory where its stored? Any help would be great. Thanks

---

### Post by cstone1983 on 2011-06-11
I was able to get the DHCP server added to webmin by changing some of the module config file. I am now having trouble starting the server, I assume some of the module config file is pointing in the wrong location can anyone tell me what their config file says.
 
I need the config file location, server executable, command to start, path to dhcp server pid file, and server lease file.

Thanks

---

### Post by Danimoth on 2011-07-05
Same problem here. Did you find a solution?

---

### Post by RickDils on 2011-07-14
I think Ubuntu 11.04 is now using a different version of DHCP, so all the config files have moved.

I installed dhcp3-server from the command line, then in Webmin found DHCP under un-used modules made the following edits:

DHCP server config file /etc/dhcp/dhcpd.conf 
DHCP server executable /usr/sbin/dhcpd 
Command to start DHCP server  /etc/init.d/isc-dhcp-server start 
Command to apply configuration  /etc/init.d/isc-dhcp-server restart 
Command to stop DHCP server  /etc/init.d/isc-dhcp-server stop 
Path to DHCP server PID file  /var/run/dhcp-server/dhcpd.pid 
DHCP server lease file /var/lib/dhcp/dhcpd.leases

Working for me anyway.

---

### Post by drifting on 2011-07-31
Following on from this. And thanks to the last poster supplying the settings, however mine seems to all work, but will not allow me to make any changes? it just ignores anything I do to DHCP?

Regards Paul

---

### Post by Techno Tony on 2012-01-17
> **drifting said:**
> Following on from this. And thanks to the last poster supplying the settings, however mine seems to all work, but will not allow me to make any changes? it just ignores anything I do to DHCP?

Regards Paul

Hi. I'm having the same problem. I've got the webmin module loaded, and the DHCP server is working, but webmin is not allowing me to save any changes to the config, or add hosts etc.

Did you get it working?

Many thanks

Tony.

---

### Post by kjv on 2012-02-13
See this URL below - it goes over the whole process of standing up a DHCP server for admin w/ Webmin:
[http://wiki.vesterling.us/index.php/Configuring_a_DHCP_Server](http://wiki.vesterling.us/index.php/Configuring_a_DHCP_Server)

There is other stuff in there too, but the Wiki was created recently (Jan 2012).


FWIW:
I too am a bit miffed that since Ubuntu 10.(?) they've re-located the DHCP configuration files, and in fact totally renamed the dhcp-server package to be "isc-dhcp-server" as of Ubuntu 11.10.

I can't help but wonder what they might call the dhcp-server package in the next major release? ;-)

Oh...  And if you use dhclient you might want to check and see that it's not going entirely bugnutz trying to store it's lease information in a directory that doesn't exist, AND trying to store it's pid in a "/var/run/dh(something)" directory that no longer exists too.  (good fun! - Still trying to figure that out.)

---

### Post by alroger on 2012-10-11
> **RickDils said:**
> I think Ubuntu 11.04 is now using a different version of DHCP, so all the config files have moved.

I installed dhcp3-server from the command line, then in Webmin found DHCP under un-used modules made the following edits:

DHCP server config file /etc/dhcp/dhcpd.conf 
DHCP server executable /usr/sbin/dhcpd 
Command to start DHCP server  /etc/init.d/isc-dhcp-server start 
Command to apply configuration  /etc/init.d/isc-dhcp-server restart 
Command to stop DHCP server  /etc/init.d/isc-dhcp-server stop 
Path to DHCP server PID file  /var/run/dhcp-server/dhcpd.pid 
DHCP server lease file /var/lib/dhcp/dhcpd.leases

Working for me anyway.

Thank you sir.
It was hard getting used to dhcp3 long time ago... now we're back to dhcp, but with ics in front of it.
Wonder if Fedora changes so much it's standards.

---

### Post by ThaDoctor72 on 2013-03-01
> **RickDils said:**
> I think Ubuntu 11.04 is now using a different version of DHCP, so all the config files have moved.

I installed dhcp3-server from the command line, then in Webmin found DHCP under un-used modules made the following edits:

DHCP server config file /etc/dhcp/dhcpd.conf 
DHCP server executable /usr/sbin/dhcpd 
Command to start DHCP server  /etc/init.d/isc-dhcp-server start 
Command to apply configuration  /etc/init.d/isc-dhcp-server restart 
Command to stop DHCP server  /etc/init.d/isc-dhcp-server stop 
Path to DHCP server PID file  /var/run/dhcp-server/dhcpd.pid 
DHCP server lease file /var/lib/dhcp/dhcpd.leases

Working for me anyway.

Excellent find. Thanks for the info. Worked great.

---

