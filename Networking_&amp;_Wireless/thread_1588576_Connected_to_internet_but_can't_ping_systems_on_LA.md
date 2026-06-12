---
title: "Connected to internet but can't ping systems on LAN"
date: 2010-10-05
forum: Networking &amp; Wireless
---

### Post by copyright201 on 2010-10-05
Hi all,

I really hope I'm not doing anything dumb here.  I've got Ubuntu 10.04 on my laptop and have recently (within the last 72 hours) started having trouble connecting to other machines on my local network.  I'm unable to ping both my router and a server set up in the room beside me.

1. I have tried pinging my server and router from other machines and it works fine.  Accessing the server via HTTP works from all machines except for my laptop.  

2. I am, however, connected to my router via wireless and can access the internet.  Also, if I connect via an ethernet cable I am able to ping both my server and router, although I'd love to be able to go wireless.

3. I assume something's wrong with my wireless setup, but I really can't figure out what.  Possibly related note: my wireless has been disconnecting unpredictably on my home network (WPA).

Any ideas?  Let me know if you'd like to see any command output and I'll get it to you asap!  I've got a Dell Studio 1558 w/ the dreaded Broadcom BCM4312 wireless controller.

```

user@blue-skies:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback

```

```

user@blue-skies:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  

```

```

user@blue-skies:~$ sudo route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.142.0      *               255.255.255.0   U     2      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         10.0.142.1      0.0.0.0         UG    0      0        0 eth1

```

```

user@blue-skies:~$ sudo lspci | grep Broadcom
04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

```

---

### Post by gzarkadas on 2010-10-05
Please post the output of the following commands: ifconfig, iwconfig, lshw (search for unclaimed hardware), cat ...syslog (search for wlan related log entries). 

The following script runs all of these, opens nano to review your syslog fragment (you may want to prune information that you deem sensitive; after finish editing press Ctrl+O, Enter, Ctrl+X) and packs all files inside an archive in your account's home folder.

```

sudo -i
mkdir -p /tmp/reports
ifconfig > /tmp/reports/ifconfig.txt
iwconfig > /tmp/reports/iwconfig.txt
lshw | grep UNCLAIMED > /tmp/reports/lshw.txt
cat /var/log/syslog|grep wlan|tail -n 200 > /tmp/reports/syslog-wlan.txt
nano /tmp/reports/syslog-wlan.txt
tar cfa /home/${SUDO_USER}/report.tar.gz /tmp/reports/*
chown ${SUDO_USER}:${SUDO_USER} /home/${SUDO_USER}/report.tar.gz
rm -R /tmp/reports
exit

```

Attach the archive to your post.

---

### Post by copyright201 on 2010-10-10
I reset my router a couple of days ago and this problem hasn't happened again since then.  If any of the same symptoms show up then I'll post back here ASAP.

No telling what setting on my router was throwing things off.  Thanks for your help anyway!

---

