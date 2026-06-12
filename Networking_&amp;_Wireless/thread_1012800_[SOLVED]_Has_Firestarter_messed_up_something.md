---
title: "[SOLVED] Has Firestarter messed up something ?"
date: 2008-12-16
forum: Networking &amp; Wireless
---

### Post by oygle on 2008-12-16
Have used Firestarter for a while now, no problems. I put it in 'lock' mode, and then later unlocked it. From then on, no internet. If I close down Firestarter, I get a connection again, and if I run Firestarter, but 'start firewall' , I can see no lights getting out to the net, and no browser results.

Has Firestarter messed up the iptables, or some other settings ? I have tried re-installing it, and also deleted all the policies, but still no go. I also re-installed the network manager, but same problem.

At present I can't use Firestarter. Any clues please, as to how to fix this.

Oygle

---

### Post by oygle on 2008-12-16
If I start Firestarter and try to access a page on this site, syslog has these entries ..

> Dec 17 00:40:08 ***** kernel: [ 3143.353998] Unknown OutputIN= OUT=ppp0 SRC=203.220.***.*** DST=203.194.***.*** LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=46925 DF PROTO=UDP SPT=55904 DPT=53 LEN=42 
Dec 17 00:40:08 ***** kernel: [ 3143.354225] Unknown OutputIN= OUT=ppp0 SRC=203.220.***.*** DST=203.194.***.*** LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=46925 DF PROTO=UDP SPT=38808 DPT=53 LEN=42 
Dec 17 00:40:08 ***** kernel: [ 3143.354402] Unknown OutputIN= OUT=ppp0 SRC=203.220.***.*** DST=203.194.***.*** LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=46925 DF PROTO=UDP SPT=43024 DPT=53 LEN=42 
Dec 17 00:40:08 ***** kernel: [ 3143.354576] Unknown OutputIN= OUT=ppp0 SRC=203.220.***.*** DST=203.194.***.*** LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=46925 DF PROTO=UDP SPT=47718 DPT=53 LEN=42 
Dec 17 00:40:08 ***** kernel: [ 3143.354780] Unknown OutputIN= OUT=ppp0 SRC=203.220.***.*** DST=203.194.***.*** LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=46925 DF PROTO=UDP SPT=36884 DPT=53 LEN=42 
Dec 17 00:40:08 ***** kernel: [ 3143.354956] Unknown OutputIN= OUT=ppp0 SRC=203.220.***.*** DST=203.194.***.*** LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=46925 DF PROTO=UDP SPT=34549 DPT=53 LEN=42 
Dec 17 00:40:08 ***** kernel: [ 3143.355131] Unknown OutputIN= OUT=ppp0 SRC=203.220.***.*** DST=203.194.***.*** LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=46925 DF PROTO=UDP SPT=59256 DPT=53 LEN=42 
Dec 17 00:40:08 ***** kernel: [ 3143.355305] Unknown OutputIN= OUT=ppp0 SRC=203.220.***.*** DST=203.194.***.*** LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=46925 DF PROTO=UDP SPT=54143 DPT=53 LEN=42 

The destination is the primary and secondary DNS IP address ??

---

### Post by oygle on 2008-12-16
This is really weird ..

1. If I don't have Firestarter running, no internet
2. If I do have Firestarter running and firewall on - no internet
3. If I do have Firestarter running, but turn off the firewall - internet

Work that out.  :confused:

---

### Post by oygle on 2008-12-16
Still the same problem.  :(

I'm connected to the internet directly with dialup (ppp0). I turned the power off on the hub/switch (eth0). This is what Firestarter says:

_Device_    _Type_

etho       Internet
ppp0       Dialup

This is when I'm connected. Why would Firestarter think that eth0 is the net ?

I try and 'start' Firestarter, and msg "Failed to start the firewall. The device eth0 is not ready.

This has got to be a networking problem, surely, but no changes were made to the network side of things.

Any clues please ?

Oygle

---

### Post by oygle on 2008-12-16
Under networking settings, if I try to 'uncheck' the wired connection (eth0), networking goes and checks it again (and starts Firestarter, which stop my internet connection).  :confused:

---

### Post by oygle on 2008-12-16
Compared the path /etc to a backup from a few days ago. Two files had significant differences ..

/etc/firestarter/configuration

backup version ..

```

#-----------( Firestarter Configuration File )-----------#

# --(External Interface)--
# Name of external network interface
IF="**ppp0**"
# Network interface is a PPP link
EXT_PPP="on"

```

Current version ..

```

#-----------( Firestarter Configuration File )-----------#

# --(External Interface)--
# Name of external network interface
IF="**eth0**"
# Network interface is a PPP link
EXT_PPP="on"

```

/etc/network/interfaces

The following line was in the backup, but was _[U]not_[/U] in the current file

```

auto eth0

```

Restored the two files, and now the network and firewall are working okay.

It pays to backup.  :D

---

