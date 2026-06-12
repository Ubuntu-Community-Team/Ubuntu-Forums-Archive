---
title: "hostname via dhcp on diskless nfs root machines, with 9.04"
date: 2009-05-26
forum: Networking &amp; Wireless
---

### Post by xdcdx on 2009-05-26
Hello,

I have several diskless machine that boot and mount the same root by NFS. I want to set them a different hostname, depending on their DHCP assigned IP.

If /etc/hostname is missing on the clients, and the dhcp server passes the hostname with 'option host-name "foobar";' the hostname is not set correclty. Instead it is set to "localhost".

Previously this little script did the trick (see this thread: [http://www.ubuntuforums.org/showthread.php?t=297530):](http://www.ubuntuforums.org/showthread.php?t=297530):)

```
#!/bin/bash

# put this file in /etc/init.d and symlink it from /etc/rcS/ just after hostname.sh

# get IP address
ip=`ifconfig | grep 'inet addr:'| grep -v '127.0.0.1' | cut -d: -f2 | cut -d' ' -f1`

# get hostname from hosts file
hostname=`cat /etc/hosts | grep $ip`
hostname=${hostname##*' '} # remove everything before the last ' '

# set hostname
echo "Hostname found:" $hostname
hostname $hostname
```

But it stopped working on 9.04. It is not working because it is being executed too soon. If I symlink at /etc/rcS.d/99h, it always fails. If I link it at /etc/rc2.d/99h it fails about 50% of times.

If I add a 'sleep 12' at the start of the scripts, it always works, but this is a wacky workaround. Can anybody enlight me so I can properly delay it so it is executed whatever prevents the hostname from being set?

---

### Post by hasanilingi on 2009-05-27
I am sorry, because i could not answer your question. i am trying to set up diskless Ubuntu. but i could not achieve it.although i try [https://help.ubuntu.com/community/DisklessUbuntuHowto](https://help.ubuntu.com/community/DisklessUbuntuHowto) and googled. In your question you say you have diskless clients. Please help me to install my server and client for diskless booting.

---

