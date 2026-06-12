---
title: "Wireless AP dropping TCP connections from Windows hosts"
date: 2009-04-27
forum: Networking &amp; Wireless
---

### Post by ergosteur on 2009-04-27
Not sure if this is the right place to post this...
I have an odd issue with my wireless network. I have a D-Link DWL-3500AP connected to a Cisco Catalyst 2950. The D-Link is advertising multiple SSIDs, each tagged with a different VLAN. The port on the Catalyst is configured to trunk mode. 

What is odd is that Linux and Mac clients can connect to any of the SSIDs and have full LAN and Internet access; Windows clients can connect but their TCP connections seem to get closed. For example, they can get an HTTP login prompt, but after submitting the username and password, the connection times out. 

Looking at the "Events" section on the AP:
Linux clients produce no error.
Windows clients cause "Jan 1 00:23:28  	 err  	 syslog  	 switch_comm_util.c:1259:map_switch_comm_util_ssl_find_error - SSL connection has been closed "

Does anyone have any idea what this could be happening? Perhaps someone can shed some light on the differences in Windows and Linux networking?

Thanks.

Edit: It seems that the problem occurs when trying to communicate across VLANs. http, rdp and vnc work when connecting to any machines in the same VLAN, but the connections seem to be terminated after a short while when the server and client are in different VLANs

---

