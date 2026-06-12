---
title: "dhcpd rndc.key Permission denied"
date: 2009-06-27
forum: Networking &amp; Wireless
---

### Post by Astrolabe on 2009-06-27
I have a problem starting DHCP on Ubuntu v9.04. I get this error after running:

sudo /etc/init.d/dhcp3-server start

[FONT="Courier New"]dhcpd self-test failed. Please fix the config file.
The error was:
Internet Systems Consortium DHCP Server V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Can't open /etc/bind/rndc.key: Permission denied[/FONT]

It does seem there has been a bug reported ([http://www.mail-archive.com/ubuntu-server-bugs@lists.ubuntu.com/msg10134.html]("http://www.mail-archive.com/ubuntu-server-bugs@lists.ubuntu.com/msg10134.html")) but after following the suggested workaround of changing permissions of both the bind directory and the rndc.key itself the problem remains.

Hopefully I have missed something really obvious. Can anyone help?

---

### Post by Astrolabe on 2009-06-27
I have found that if I disable AppArmor the problem goes away. I am not sure what the implications of this will be but if AppArmor proves to be unnecessary I will remove it permanently and this thread will be resolved.

---

### Post by Astrolabe on 2009-06-27
OK – I have completely fixed this problem. I have added these two lines to the dhcp3 profile: /etc/apparmor.d/usr.sbin.dhcpd3

  /etc/bind/ r,
  /etc/bind/** r,

After restarting apparmor I am now able to restart dhcp3 without any errors.

---

### Post by Astrolabe on 2009-06-27
I had to make one last minor change to /etc/apparmor.d/usr.sbin.dhcpd3:

/etc/bind/ rw,
/etc/bind/** rw,

This allows dynamic updates to the DNS zone files (unless I should have put them somewhere else - but this works).

---

### Post by robert.mcnutty on 2010-02-01
I had to change the owner and file permissions on the rndc.key file from bind:bind to root:bind and -rw-r---r--. 

sudo chown root:bind /etc/bind/rndc.key
sudo chmod 644 /etc/bind/rndc.key

---

### Post by kWahab on 2010-05-27
Changed the group to "dhcpd" for rndc.key

sudo chgrp dhcpd /etc/bind/rndc.key

This way the key file is not readable by everyone.

---

### Post by logiconcepts819 on 2010-08-05
By the way, I think I found the culprit of the problem.  If you happen to download the source for dhcp3 using apt-get, you will find two offending patches in the source directory:

debian/patches/droppriv.dpatch
debian/patches/deroot-server.dpatch

The second patch will change the effective user ID and effective group ID of the server process to dhcpd and dhcpd, respectively, which means that even if dhcpd was launched as root, the program will act as if it had been launched by the user dhcpd.  Therefore, the best you can do is to set the owners of the rndc.key file to the bind user and the dhcpd group and permitting them to read the file only (i.e. chown bind.dhcpd /etc/bind/rndc.key; chmod 440 /etc/bind/rndc.key). It's a rather horrible hack, but it seems to work.

---

