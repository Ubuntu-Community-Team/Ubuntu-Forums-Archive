---
title: "Cinerela?"
date: 2007-11-02
forum: Multimedia Production
---

### Post by m005k on 2007-11-02
Is there a Cinerela that will work with with Ubuntu?

Mike

---

### Post by Dai777 on 2007-11-03
Yes
[http://www.kiberpipa.org/~muzzol/cinelerra/feisty-i386/](http://www.kiberpipa.org/~muzzol/cinelerra/feisty-i386/)

Down load the following

 cinelerra_2.1.0+svn20070109-0ubuntu1_i386.deb 
 libguicast_2.1.0+svn20070109-0ubuntu1_i386.deb 
libmpeg3hv_2.1.0+svn20070109-0ubuntu1_i386.deb 
libquicktimehv_2.1.0+svn20070109-0ubuntu1_i386.deb 

after installing if you get a memory warning open up the terminal and type in the following:

sudo gedit /etc/sysctl.conf

and put:
**kernel/shmmax=0x7fffffff**
at the bottom of the file and save it

my file:
#
# /etc/sysctl.conf - Configuration file for setting system variables
# See sysctl.conf (5) for information.
#

#kernel.domainname = example.com
#net/ipv4/icmp_echo_ignore_broadcasts=1

# the following stops low-level messages on console
kernel.printk = 4 4 1 7

# enable /proc/$pid/maps privacy so that memory relocations are not
# visible to other users.
kernel.maps_protect = 1

##############################################################3
# Functions previously found in netbase
#

# Uncomment the next line to enable Spoof protection (reverse-path filter)
#net.ipv4.conf.default.rp_filter=1

# Uncomment the next line to enable TCP/IP SYN cookies
#net.ipv4.tcp_syncookies=1

# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.conf.default.forwarding=1

# Uncomment the next line to enable packet forwarding for IPv6
#net.ipv6.conf.default.forwarding=1
kernel/shmmax=0x7fffffff

---

