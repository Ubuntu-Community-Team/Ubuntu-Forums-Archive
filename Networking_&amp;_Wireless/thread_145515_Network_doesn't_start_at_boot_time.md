---
title: "Network doesn't start at boot time"
date: 2006-03-16
forum: Networking &amp; Wireless
---

### Post by /dev/urandom on 2006-03-16
Actually the script /etc/init.d/networking should be run while booting. But after logging in I can't ping:
```
$ ping 193.99.144.80
connect: Network is unreachable 
```
With
```
$ sudo /etc/init.d/networking restart
```
or start and stop the network gets started without any problems, so the script should be ok.
So what's wrong when it is run at boot time?
Wrong order of /etc/rcS.d skripts?
```
$ ls /etc/rcS.d/
README                              S27evms         S40ifrename
S02mountvirtfs                      S30checkfs.sh   S40networking
S04mdadm-raid                       S30procps.sh    S41hotplug-net
S04udev                             S35mountall.sh  S45mountnfs.sh
S05bootlogd                         S35quota        S48console-screen.sh
S05keymap.sh                        S36mountvirtfs  S50alsa-utils
S07hdparm                           S36udev-mtab    S50hwclock.sh
S10checkroot.sh                     S38pppd-dns     S55bootmisc.sh
S15linux-restricted-modules-common  S39dns-clean    S55urandom
S18ifupdown-clean                   S39ifupdown     S70screen-cleanup
S20module-init-tools                S39readahead    S70xorg-common
S22hwclockfirst.sh                  S40hostname.sh  S75sudo
S26lvm                              S40hotplug
```

---

