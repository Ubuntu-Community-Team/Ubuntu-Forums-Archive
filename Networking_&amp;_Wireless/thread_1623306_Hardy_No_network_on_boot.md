---
title: "Hardy: No network on boot"
date: 2010-11-16
forum: Networking &amp; Wireless
---

### Post by x1a4 on 2010-11-16
Hi,

My network doesn't work on boot.  I have to ifdown then ifup before it starts working again.  Any ideas on how to diagnose this? 

Thank you.

---

### Post by x1a4 on 2010-11-18
Bump :(

---

### Post by grahammechanical on 2010-11-19
I am not familiar with the menus and dialogs of Hardy. Are your connections set to connect automatically? Do you see any kind of network icon? Things have improved since Hardy was released.

Regards.

---

### Post by x1a4 on 2010-11-19
Thank you for your reply.  Yes, it is supposed to connect automatically and it did for a long time.  I'm using Wicd as my network manager but this is not related to that.  I suspect this is an issue at the kernel.  I think the network card driver doesn't load correctly.  All my network settings are correct and things work fine, except during boot when the network interface doesn't come up.  Once I run **sudo ifdown eth0** followed by **sudo ifup eth0** it works.  Using ifup only, tells me the interface is already configured.  

This is a wired connection.  The card is an on-board VIA VT6102.  
System logs (syslog, dmesg, messages, kern.log, daemon.log, etc.) show no errors. Wicd's log states that there is no wired connection and after several attempts to connect it fails, requiring me to connect manually.  

Don't worry about Hardy menus and such.  If I know what to do I'm sure I can figure out how to do it (If only by asking here :) ).  I'm also comfortable with the command line.

---

### Post by grahammechanical on 2010-11-19
Here is the link to the trouble shooting guide

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

I know it is wireless and you are on wire but some of the commands in the guide provide information on ethernet connections. 

Is there some way of saving the current session in Hardy? I know it seems unrelated but the other day I was checking out a suggestion for fixing the problem of wireless connections not coming back up after a suspend or hibernation. Saving the current session seemed to work.

Regards.

You can also check System>Preferences>Startup Applications and see if network manager has a tick mark against it. If not then that could be it.

---

### Post by x1a4 on 2010-12-19
Thank you, but alas, it didn't help.  

I did notice that /etc/init.d/networking does run successfully (at least it doesn't throw an error) but later eth0 keeps entering then leaving promiscuous mode finally ending in promiscuous mode.  Most recent log entries are: 
```

Dec 19 19:56:47 linbox kernel: [   60.976983] ppdev: user-space parallel port driver
Dec 19 19:56:47 linbox kernel: [   61.182109] audit(1292806607.644:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5513 profile="/usr/sbin/cupsd" namespace="default"
Dec 19 19:56:49 linbox kernel: [   63.208269] device eth0 entered promiscuous mode
Dec 19 19:56:49 linbox kernel: [   63.208285] audit(1292806609.676:3): dev=eth0 prom=256 old_prom=0 auid=4294967295
Dec 19 19:56:49 linbox kernel: [   63.224179] device eth0 left promiscuous mode
Dec 19 19:56:49 linbox kernel: [   63.224190] audit(1292806609.692:4): dev=eth0 prom=0 old_prom=256 auid=4294967295
Dec 19 19:56:49 linbox kernel: [   63.236169] device eth0 entered promiscuous mode
Dec 19 19:56:49 linbox kernel: [   63.236188] audit(1292806609.704:5): dev=eth0 prom=256 old_prom=0 auid=4294967295
Dec 19 19:56:52 linbox dhcdbd: Started up.

```

I also noticed that invoking /etc/init.d/networking directly or using invoke-rc.d doesn't help.  Neither does starting the network card in /etc/rc.local

Could somehow wicd (network-manager replacement) be interfering with the networking script?  I tried loading it in various stages during boot including before and after wicd, but so far without any luck.  ](*,)

---

### Post by x1a4 on 2011-01-09
B.U.M.P.  Any ideas anyone:?:

---

