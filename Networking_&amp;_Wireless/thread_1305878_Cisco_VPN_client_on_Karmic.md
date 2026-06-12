---
title: "Cisco VPN client on Karmic"
date: 2009-10-30
forum: Networking &amp; Wireless
---

### Post by supermoro on 2009-10-30
Hi everybody,
I found a solution for my little problem and want to share with you.

Cisco Vpn worked fine until i passed to 9.10.
Normally, on kernel updates, i had to re-install VpnClient, to make sure the app would take the correct path (that includes the kernel name)

This time it didn't work. 

I found this page [http://ilapstech.blogspot.com/2009/09/cisco-vpn-client-on-karmic-koala.html ]("http://ilapstech.blogspot.com/2009/09/cisco-vpn-client-on-karmic-koala.html")and it explains the thing quite well, and, of course, it works.

Hope this will help somebody.

See you all

---

### Post by Grim76 on 2009-10-30
One thing that you might want to look into is vpnc for connecting to your VPN. It is working for me with our Cisco devices.

[http://www.ubuntugeek.com/how-to-setup-cisco-vpn-using-vpnc-ubuntu-jaunty-9-04.html](http://www.ubuntugeek.com/how-to-setup-cisco-vpn-using-vpnc-ubuntu-jaunty-9-04.html)

Just another approach that might work for you.

---

### Post by cuby on 2009-11-02
hello, 
try [this]("http://ubuntuforums.org/showthread.php?t=1311289") post.

---

### Post by Benic on 2009-11-10
Thanks supermoro, it works perfectly!

---

### Post by fargle on 2009-11-10
I believe that VPNC doesn't support IPSEC over TCP, though, so it might not be compatible with quite a few places that were running VPN before the whole NAT-T thing started up.  IPSEC over TCP is Cisco-only and uses port 10000 TCP.

Just FYI, Cisco AnyConnect (the Cisco SSL VPN client) installs and works perfectly on Karmic as well with nothing to tweak.

---

