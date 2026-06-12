---
title: "Forwarding to a transparent proxy from Netgear router"
date: 2011-04-23
forum: Networking &amp; Wireless
---

### Post by dawbomb on 2011-04-23
Hi All,

I've set up a squid3 proxy on my server, which I would ideally like to make transparent.  My router is a Netgear DG834GUv5, which runs Busybox Linux.

As I understand it, normally one would use iptables to forward everything to the proxy.  This router does not seem to have iptables installed...  Where to from here?

I don't want EVERYTHING to be forwarded to the proxy server - only HTTP traffic, and I would like to retain the IP address of the user's computer for logging purposes.

Essentially I would like:
User's computer -> router -> proxy -> router -> internet

The list of commands I have to work with:
```
~ # help

Built-in commands:
-------------------
        . : [ [[ alias bg break cd chdir continue echo eval exec exit
        export false fg hash help jobs kill let local pwd read readonly
        return set shift source test times trap true type ulimit umask
        unalias unset wait

~ # version
Release version : Netgear Wireless ADSL Router DG834GUv5
                  U12L06000/TKV6.00.26
           Time : Apr  3 2009 08:33:16
~ # ls /bin 
VeriSign2028RootCA.cer  kill                    sleep
ash                     ln                      startasterisk
automount               ls                      startbif
bftpd                   mkdir                   startbsp
busybox                 mknod                   startdslbridge
cat                     mount                   startminbsp
chgrp                   mv                      startnat
chmod                   netstat                 startppp
chown                   paed                    startusb
cp                      pda-rw                  startwhip
date                    ping                    startwps
df                      ps                      swapdev
du                      pwd                     sys_restart
echo                    qsh                     tar
egrep                   read-truepda            test
ethtool                 respawnd                umount
fgrep                   rm                      uname
flash_eraseall          rmdir                   verify_flash
flash_update            rpaed                   wget
getoid                  rssid                   wpin
grep                    scanpvc                 writemac
halt                    setoid                  wsccmd
insmod                  sh
~ # ls /sbin
acos_init        burnsn           lsmod            route
acos_service     cert             modprobe         syslogd
atmarp           halt             ntpclient        uptime
atmarpd          ifconfig         poweroff         vconfig
bd               init             read_bd          version
burnboardid      insmod           reboot
burnethermac     ipoa-up          reset_no_reboot
burnpin          klogd            rmmod
```

Thanks in advance!

---

