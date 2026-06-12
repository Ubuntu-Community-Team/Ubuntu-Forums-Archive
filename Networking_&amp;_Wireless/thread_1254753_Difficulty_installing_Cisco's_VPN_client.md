---
title: "Difficulty installing Cisco's VPN client"
date: 2009-08-31
forum: Networking &amp; Wireless
---

### Post by DemaSRV on 2009-08-31
I'm a student at Purdue and in order to connect to our VPN servers they have a client that is available (cisco's vpn client).  I've downloaded it and whenever I try to install it this is what I get.

```

tyler@tyler-laptop:~/Downloads$ sudo vpnclient/vpn_install
Cisco Systems VPN Client Version 4.8.01 (0640) Linux Installer
Copyright (C) 1998-2006 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms. 


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.28-15-generic/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.28-15-generic/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.28-15-generic/build" will be used to build the module.

Is the above correct [y]

Making module
sh: Can't open ./driver_build.sh
Failed to make module "cisco_ipsec.ko".

```

I don't know where to go from here to get it to work, I think I've installed all of the dependencies.

[http://www.cisco.com/en/US/docs/security/vpn_client/cisco_vpn_client/vpn_client46/linux_solaris/uglinsol.html](http://www.cisco.com/en/US/docs/security/vpn_client/cisco_vpn_client/vpn_client46/linux_solaris/uglinsol.html)

that is cisco's user guide for the software.

Thanks in advance for any help you can provide.

---

### Post by DemaSRV on 2009-08-31
Tech support just emailed me this, I asked them to send me the VPN server settings I needed since I had vpnc installed.

> Hi Tyler,

Please try these settings if you are having trouble with the Cisco Client for Linux:

Pre-Shared Key for authentication: PurdueVPN
Type of VPN: L2TP IPSec VPN

Or you can try using vpn.purdue.edu as your VPN Internet Address.  Please give those a try.  Thanks and have a great day!

---

