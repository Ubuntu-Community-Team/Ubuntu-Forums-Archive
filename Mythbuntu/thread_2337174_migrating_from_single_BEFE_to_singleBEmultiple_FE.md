---
title: "migrating from single BE/FE to singleBE/multiple FE"
date: 2016-09-15
forum: Mythbuntu
---

### Post by Nate B. on 2016-09-15
I have a single machine BE/FE installation running 14.04.5 and it is working well.  Everything is configured for 127.0.0.1/localhost.  I would like to reconfigure the BE/database to accept connections over my LAN.  I know that will affect the settings in the FE of the present installation as well.

Has someone done this and written a mini-HOWTO on it?  I know that configuration is scattered between /etc/mysql, /etc/mythtv, and ~/.mythtv but am unsure of what order I should modify the configurations and whether it is a just a simple matter of replacing 127.0.01/localhost with the external IP address/LAN hostname and restarting the services.

TIA

---

### Post by Nate B. on 2016-09-15
Turned out to be rather easy.

Made sure the frontend wasn't running.

Started Mythbuntu Control Centre and enabled Mysql to listen on the network interface.

Reconfigured the backend General settings for the local backend network interface IPv4 and IPv6 addresses, set the master backend to the network interface IPv4 address.  Left other settings as they were and restarted the backend.

Quit MCC and started the frontend.

In the frontend setup->general settings, set the Hostname to the backend's hostname (I have a local DNS server for my LAN, otherwise the IPv4 address should work, perhaps the IPv6 address set earlier as well).  Set the custom identifier to a unique name and left all other settings as they were.  Finally made sure recordings and live TV could be watched.

The final test was being able to install the mythtv-frontend package from deb.multimedia.org on my Devuan Jessie desktop and having a successful connection to the backend to watch recordings.

Most likely it probably would have been easier to set it up in this manner in the first place.

---

