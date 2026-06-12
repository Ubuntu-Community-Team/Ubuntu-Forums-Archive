---
title: "Cisco AnyConnect problem"
date: 2009-10-14
forum: Networking &amp; Wireless
---

### Post by pmdserrano on 2009-10-14
Good Day,

I'm new in Ubuntu. I just formatted my machine because I always got a virus from Windows platform. :(

I want to install Cisco VPN AnyConnect, so I downloaded anyconnect-linux-2.3.2016-k9.tar.gz. I install it using by

sudo ./vpn_install.sh

After doing that, I could see it has been installed in my Application > Internet > Cisco AnyConnect VPN Client.

My problem is, everytime I'm trying to login to our company's VPN, there is an error of:

"AnyConnect package unavailable or corrupted. Contact your system administrator."

Is it a problem of my connection? Or a problem with my installation of AnyConnect?
Because I tried connecting through our company's VPN using my friend's machine which also have AnyConnect but on Windows Vista platform and it went perfectly well.

By the way, my machine is running on 32 bit.

Thanks,
Paul

---

### Post by casevh on 2009-10-17
IIRC, this error can be caused if the Linux package is not installed, or is corrupt, on the remote access server. The server compares your version with its versions and will try to upgrade/downgrade your system to match the version(s) on the server.

If sys admin is Linux friendly, or at least Linux tolerant, ask if they will install the Linux package on server.

casevh

---

