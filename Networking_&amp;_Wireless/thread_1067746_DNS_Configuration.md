---
title: "DNS Configuration"
date: 2009-02-12
forum: Networking &amp; Wireless
---

### Post by Drenriza on 2009-02-12
I've tryed to change my DNS configuration but so far without luck.

I've tryed Network connection -> edit -> IPv4 Settings -> DNS Servers: 208.67.222.222, 208.67.220.220 -> ok

But after reboot the DNS settings is removed, and Automatic DHCP is again enabled.

to resolve this i then tryed.

To avoid having your settings get revoked after reboots, or after periods of inactivity you may need to make the following changes via the command line:

    $ sudo cp /etc/resolv.conf /etc/resolv.conf.auto
    $ gksudo gedit /etc/dhcp3/dhclient.conf
    # append the following line to the document
    prepend domain-name-servers 208.67.222.222,208.67.220.220;
    # save and exit
    $ sudo ifdown eth0 && sudo ifup eth0 

But sudo cp /etc/resolv.conf /etc/resolv.conf.auto is unable to resolve host. Then what can you do to keep the DNS changes?

Thanks on advance

---

### Post by superprash2003 on 2009-02-12
hope this helps [http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by Drenriza on 2009-02-14
> **superprash2003 said:**
> hope this helps [http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html)

Thanks alot, i've tryed forever to get this to work :) and now it does.
Great toturial, Thanks mate.:P

---

