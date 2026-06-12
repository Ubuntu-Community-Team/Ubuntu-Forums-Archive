---
title: "DHCPD can't include file in another place"
date: 2012-05-17
forum: Networking &amp; Wireless
---

### Post by rockballad on 2012-05-17
Hello,

I'm trying to include a file in my home folder by specifying the path in dhcpd.conf file. However, DHCPD doesn't accept it. The problem is:

dhcpd self-test failed. Please fix the config file.
The error was: 
Internet Systems Consortium DHCP Server V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Can't open /home/user/abc.entry: Permission denied

But when I copy abc.entry to /etc/dhcp3/, it works normally. 

Anything wrong here? Is it possible to include a file outside DHCP home dir (/etc/dhcp3)?

Thanks for any answer.

---

### Post by davetv on 2012-05-17
You could try making a symlink to the other file.

In a terminal enter  :-

sudo ln -s ~/abc.entry /etc/dhcp3/abc.entry

---

### Post by rockballad on 2012-05-17
Thank you... I've tried but it still shows the same error. Could you please give it a try?

The sample file content to be included looks like this:

host pub01 {
  hardware ethernet A2:AA:BB:05:60:3E;
  fixed-address 172.20.6.10;
  option host-name "pub01";
  option subnet-mask 255.255.255.0;
  option routers 172.20.6.1;
  option broadcast-address 172.20.6.255;
  option domain-name-servers 192.168.0.1;
}

---

### Post by davetv on 2012-05-17
I don't run a recent ubuntu version, and I don't have the same file, so I can't really test it. For the most part symlinks work in this kind of situation.

Sorry I can't help further.

---

### Post by rockballad on 2012-05-17
Thank you for helping me so far, davetv!

---

### Post by davetv on 2012-05-17
The last thing I can think of is that the file abc.entry in your home folder is owned by root and/or has insufficient permissions for the file to be read. (I can't see why it would require write access), and the process is launched as a user.

After my above post, did the symlink appear in /etc/dhcp3 ?

A quick test to change permissions would be 

sudo chmod 666 /home/user/abc.entry

followed by generating the symlink 

sudo ln -s /home/user/abc.entry /etc/dhcp3/abc.entry

Which should give all users read write permissions on the file. Not sure if this would help but worth a go.

Good luck.

---

### Post by rockballad on 2012-05-17
You're so kind. I did as you said. I also change owner "chown" of abc.entry to "user:user" or "user:dhcpd" and "root:root" but it doesn't help. Is it strange, isn't? All files in /etc/dhcp3/ are root:root. I change it to user:user but still the same problem.

Thank you again, anyway!

---

### Post by rockballad on 2012-05-21
Look like Ubuntu doesn't support this so far. On other distro, it may be ok but I need to disable SELinux first.

Thanks and regards,

---

### Post by steeldriver on 2012-05-21
do you have multiple partitions? if so maybe dhcpd is starting before your home dir is mounted?

---

### Post by rockballad on 2012-05-21
> **steeldriver said:**
> do you have multiple partitions? if so maybe dhcpd is starting before your home dir is mounted?


Hi, no, just single partition. Suppose it's started, but I can restart anytime. I don't understand the connection you made yet.

Thanks for the input.

Cheers,

---

