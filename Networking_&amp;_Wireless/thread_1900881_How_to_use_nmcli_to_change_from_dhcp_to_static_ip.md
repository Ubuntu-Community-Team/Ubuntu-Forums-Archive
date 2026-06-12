---
title: "How to use nmcli to change from dhcp to static ip ?"
date: 2011-12-27
forum: Networking &amp; Wireless
---

### Post by ningji on 2011-12-27
Hi, with network manager, seems /etc/sysconfig/interfaces is obsolete.

If i want to change from dhcp to static ip using command line,
how to do it in nmcli (or whatever) ?

this is ubuntu 11.04.

thanks !

---

### Post by DrTebi on 2012-12-13
> **ningji said:**
> Hi, with network manager, seems /etc/sysconfig/interfaces is obsolete.

If i want to change from dhcp to static ip using command line,
how to do it in nmcli (or whatever) ?

this is ubuntu 11.04.

thanks !

Hi,

I have been trying to do the same. So far I haven't figured out how to do it with nmcli, but here is my approach to do it with a script. I wrote a bunch of extra comments into the file, which should explain what each line does:

```

#!/bin/bash

# stop NetworkManager
stop network-manager

# copy the NetworkManager.conf file to tmp.txt, so that it can be
# modified with sed, which will write its output into the original
# NetworkManager.conf file
cp /etc/NetworkManager/NetworkManager.conf /etc/NetworkManager/tmp.txt
sed 's/true/false/g' /etc/NetworkManager/tmp.txt > /etc/NetworkManager/NetworkManager.conf
rm -rf /etc/NetworkManager/tmp.txt

# put all network info into /etc/network/interfaces
echo >> /etc/network/interfaces "
iface eth0 inet static
address 192.168.0.20
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1
"

# add nameserver to /etc/resolv.conf
echo 'nameserver 8.8.8.8' >> /etc/resolv.conf

# restart networking
/etc/init.d/networking restart

# get out of gnome-session, this is necessary to
# get NetworkManger to stop and use the manual entries
sudo -u ubuntu DISPLAY=:0 gnome-session-quit --force

# Finally bring up network connection for eth0
ifup eth0

```

Of course you will have to replace the IP numbers with the ones of your setup. Then name this script e.g. network-setup.sh and make it executable. You must run this script with sudo...
```
sudo network-setup.sh
```

Note that I am using Ubuntu 12.04, and the Gnome-Shell; it also assumes that you are logged in as regular user. You may have to edit the logout command if you are using unity or else-what. Not sure if this works on 11.04, but it does work on 12.04.

The script will log you out once it has run all commands--as mentioned above, this is necessary to get everything running.

It would be much more elegant to use nmcli for this though. The problem is a) that you are disabling the Network Manager altogether, and b) that you will have to login again after the script runs.

My reason for writing this script was to quickly setup networking when using a live-cd. It's faster to run this script than to go through the dialogs... especially on a laptop.

DrTebi

---

