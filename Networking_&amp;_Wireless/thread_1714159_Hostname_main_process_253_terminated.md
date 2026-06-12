---
title: "Hostname main process 253 terminated"
date: 2011-03-25
forum: Networking &amp; Wireless
---

### Post by 8dogsbarking on 2011-03-25
I edited my etc/hostname file, and now I get the following error:
*Hostname main process 253 terminated with status 1*

This comes up when I reboot.  AND, now that this started, I have to restart my smbd manually to get my windows 7 laptop to connect to my USB hard drive.  WHAT GIVES???!!!

Here is my hostname readout:

ubuntu@ubuntu_pc:~$ cat /etc/hosts
192.168.0.54    ubuntu_pc    # Added by NetworkManager
127.0.0.1    localhost.localdomain    localhost
::1    ubuntu_pc    localhost6.localdomain6    localhost6
127.0.1.1    ubuntu_pc

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

