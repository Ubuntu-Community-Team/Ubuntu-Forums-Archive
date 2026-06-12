---
title: "DVD/BR through iSCSI"
date: 2011-04-25
forum: Networking &amp; Wireless
---

### Post by SkoFeller on 2011-04-25
Hello everybody!

The summary: I want to use a drive in my server on my laptop employing iSCSI. Everything appears to work, but the drive doesn't show up!

Here's the setup: A homeserver (192.168.1.2/24) running Ubuntu Server Maverick Meerkat and a Laptop (192.168.1.x/24) running Ubuntu Desktop Maverick Meerkat. They are connected through Gigabit Ethernet with a Netgear Router.

The Server has a BluRay-Drive (/dev/scd0) I want to use on the Laptop via iSCSI. I have configured both computers acccording to [http://www.howtoforge.com/using-iscsi-on-ubuntu-10.04-initiator-and-target.]("http://www.howtoforge.com/using-iscsi-on-ubuntu-10.04-initiator-and-target")

The Server uses the package iscsitarget with the following configuration:

1. /etc/default/iscsitarget says 
```
ISCSITARGET_ENABLE=true
```2. /etc/iet/ietd.conf contains
 ```
#lines and lines of comments
Target iqn.2015-12.loc.appelserv:optdisc
    Lun 0 Path=/dev/scd0,Type=blockio
```3. /etc/iet/initiators.allow lists
```
#more comments
iqn.2015-12.loc.appelserv:optdisc 192.168.1.0/24

```4. /etc/iet/targets.allow lists
```
#even moar comments
ALL ALL

```After installing the package open-iscsi on the laptop I have changed /etc/iscsi/iscsid.conf to say
```
#stuff
node.startup = automatic
#more stuff
```I have then run
```
iscsiadm -m discovery -t st -p 192.168.1.2
```which returned
```
192.168.1.2:3260,1 iqn.2015-12.loc.appelserv:optdisc
```Running
```
iscsiadm -m node
```equally returns
```
192.168.1.2:3260,1 iqn.2015-12.loc.appelserv:optdisc
```If I run
```
iscsiadm -m node --login -T iqn.2015-12.loc.appelserv:optdisc
```I get
```
Logging in to [iface: default, target: iqn.2015-12.loc.appelserv:optdisc, portal: 192.168.1.2,3260]
iscsiadm: Could not login to [iface: default, target: iqn.2015-12.loc.appelserv:optdisc, portal: 192.168.1.2,3260]: 
iscsiadm: initiator reported error (15 - already exists)

```which makes sense, since it should log in to targets automatically, and tells me that a connection exits.

So here's the problem (finally :| ):

After doing alll that and apparently connecting to the target, it is my understanding that I should now see the Drive somewhere...probably in /dev. I don't. Neither does it appear anywhere else I thought to look.

So, If anyone could tell me where else to look or what could be wrong with my configuration or where to read up on the topic of optical drives and iSCSI, I'd be very thankful!

Thank you in advance,

Jesko

---

### Post by SkoFeller on 2011-05-05
OK, I still haven't made any progress whatsoever.

I guess I'll ask the most basic question first: Is it even possible to use iSCSI on an optical drive in Ubuntu? I've yet to find a manual that covers anything but image files and hard drive partitions...

---

### Post by boshkash1151 on 2012-04-01
I am having the same problem. 
Can anyone help ?
thanks

---

### Post by boshkash1151 on 2012-04-08
If anyone faced the same problem I used tgt

[SIZE="2"]install[/SIZE] 
```
sudo apt-get install tgt
```

[SIZE="2"]start service [/SIZE]
```
sudo service tgt start
```

[SIZE="2"]configuration[/SIZE]

add target
```
tgtadm --lld iscsi --op new --mode target --tid 1 -T iqn.2010-01.us.nimsa:tgt:4:16:0:0:T
```

add device
```
tgtadm --lld iscsi --op new --mode logicalunit --tid 1 --lun 1 --bstype=sg --device-type=pt -b /dev/sg1
```

you can get the device path by using the following command 
```
lsscsi -g
```

Allow target to accept initiator connections
```
tgtadm --lld iscsi --op bind --mode target --tid 1 -I ALL
```


credits go to and for more details and configurations
```

http://www.cyberciti.biz/tips/howto-setup-linux-iscsi-target-sanwith-tgt.html
http://mhvtl-linux-virtual-tape-library-community-forums.966029.n3.nabble.com/MHVTL-0-18-10-tgt-iSCSI-target-td1684577.html
http://linux.die.net/man/8/tgtadm

```

---

