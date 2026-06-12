---
title: "OpenDNS setup problems"
date: 2009-06-15
forum: Networking &amp; Wireless
---

### Post by Ryanmt on 2009-06-15
The dns servers on my vps are down so ive been told to use the opendns ones.

edit resolv.conf with opendns ip's reboot.. the files changed back.

So i edit dhclient.conf and add

supersede (also tried prepend) domain-name-servers xx,xx;

Reboot and resolv its changed back.. adding the line to dhclient.conf makes no difference

so i go into /etc/sysconfig/network-scripts and edit the two files vnet0 and vnet0:0 (2 ip's) and add PEERDNS=no.

Reboot, resolv.conf and the two files ive edited have changed back to orginal.

Im pulling my hair out since i cant resolve anything to send emails etc, and its starting to feel alot like groundhog day.

Now ive tried to Manually edit /etc/resolv.conf and then chattr +i /etc/resolv.conf.

Reboot and its not changed but

```
 sudo cat /etc/resolv.conf
#search lan
nameserver 208.67.222.222 
nameserver 208.67.222.220
ryanmt@vps:~$ ping google.com
ping: unknown host google.com
ryanmt@vps:~$ ping 208.67.222.222
PING 208.67.222.222 (208.67.222.222) 56(84) bytes of data.
64 bytes from 208.67.222.222: icmp_seq=1 ttl=58 time=1.44 ms
64 bytes from 208.67.222.222: icmp_seq=2 ttl=58 time=1.45 ms

--- 208.67.222.222 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 1.449/1.453/1.458/0.038 m

```

any ideas? :(

Ps, its on a server so command line only suggestions please :)

---

### Post by scrooge_74 on 2009-06-15
OPENDNS instructions work for me


To avoid having your settings get revoked after reboots, or after periods of inactivity you may need to make the following changes via the command line:

    $ sudo cp /etc/resolv.conf /etc/resolv.conf.auto
    $ gksudo gedit /etc/dhcp3/dhclient.conf
    # append the following line to the document
    prepend domain-name-servers 208.67.222.222,208.67.220.220;
    # save and exit
    $ sudo ifdown eth0 && sudo ifup eth0 

You may be required to change eth0 to your own network device's name if it uses a non-standard name.

---

### Post by Ryanmt on 2009-06-16
Yep tried all that first, didnt make any difference atall. Nor did editing resolv.conf.. its very weird. Its on a vps so im not sure if its taking config off the host machine or something.

---

