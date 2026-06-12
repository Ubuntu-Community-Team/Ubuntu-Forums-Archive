---
title: "Cisco vpnclient problem starting"
date: 2009-06-05
forum: Networking &amp; Wireless
---

### Post by PerfectReign on 2009-06-05
I recently moved over to Ubuntu 9.04 (Was there a 9.03?) from openSUSE 10.3.  I routinely work from home (like today) and connect using either a Juniper web-based sslvpn solution or using the cisco vpnclient. I'd rather use the easier web-based Juniper vpnclient but I cannot get remote desktop working using that solution.

I installed teh latest vpnclient and have it working. I'd even written a blog entry - [http://www.perfectreign.com/?q=node/95](http://www.perfectreign.com/?q=node/95) - on how to do this in openSUSE. I've also searched google and here and can't find the solution I'm looking for.

Here's teh issue; When I go to launch the vpnclient, I get the message:

[FONT=Courier New]root@r2d2:/home/kai# vpnclient connect lacrr
Cisco Systems VPN Client Version 4.8.02 (0030)
Copyright (C) 1998-2007 Cisco Systems, Inc. All Rights Reserved.
Client Type(s): Linux
Running on: Linux 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686
Config file directory: /etc/opt/cisco-vpnclient

Could not attach to driver. Is kernel module loaded?
The application was unable to communicate with the VPN sub-system.[/FONT]

Of course, I simply can run vpnclient_init to load the subsystem:

[FONT=Courier New]root@r2d2:/opt/cisco-vpnclient/bin# /etc/init.d/vpnclient_init restart
Shutting down /opt/cisco-vpnclient/bin/vpnclient: module cisco_ipsec is not running.
Starting /opt/cisco-vpnclient/bin/vpnclient: Done[/FONT]

and all works from there.

After that I connect without a problem:

[FONT=Courier New]root@r2d2:/opt/cisco-vpnclient/bin# vpnclient connect lacrr
Cisco Systems VPN Client Version 4.8.02 (0030)
Copyright (C) 1998-2007 Cisco Systems, Inc. All Rights Reserved.
Client Type(s): Linux
Running on: Linux 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686
Config file directory: /etc/opt/cisco-vpnclient

Initializing the VPN connection.
Contacting the gateway at 8.5.2.1
User Authentication for lacrr...

The server has requested the following information to complete the user authentication:

Username [e515421]: 
Password []: 
Authenticating user.
Negotiating security policies.
Securing communication channel.

Your VPN connection is secure.

VPN tunnel information.
Client address: 1.3.1.1
Server address: 8.5.2.1
Encryption: 168-bit 3-DES
Authentication: HMAC-SHA
IP Compression: None
NAT passthrough is active on port UDP 4500
Local LAN Access is disabled
[/FONT]


The thing I want to know is - why isn't the kernel module loading at boot? Where in Ubuntu can I find what gets loaded at boot and how to I set the system to load this?

---

### Post by casevh on 2009-06-06
If I remember correctly, Cisco assumes a particular runlevel and Ubuntu starts a different runlevel. I think I created a symlink to vpnclient_init from the other runlevels.

If you need more details, I can install it again. 

casevh

---

