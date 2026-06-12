---
title: "Jaunty 9.04 intermittent wired problem"
date: 2009-04-25
forum: Networking &amp; Wireless
---

### Post by PPPP on 2009-04-25
I just upgraded from 8.10 Ibex to 9.04 Jaunty.  I noticed my wired connection is not stable.  Taking a look at /var/log/messages, I saw something as follows:

```

Apr 25 23:33:36 plui-amd64-ubuntu kernel: [104505.220674] eth0: link down.
Apr 25 23:33:38 plui-amd64-ubuntu kernel: [104506.864627] eth0: link up.
Apr 25 23:33:38 plui-amd64-ubuntu kernel: [104506.868478] eth0: link down.
Apr 25 23:33:40 plui-amd64-ubuntu kernel: [104508.542144] eth0: link up.
Apr 25 23:33:43 plui-amd64-ubuntu kernel: [104512.266598] eth0: link down.
Apr 25 23:33:45 plui-amd64-ubuntu kernel: [104514.048507] eth0: link up.
Apr 25 23:34:04 plui-amd64-ubuntu kernel: [104532.555333] eth0: link down.
Apr 25 23:34:05 plui-amd64-ubuntu kernel: [104534.213331] eth0: link up.
Apr 25 23:34:06 plui-amd64-ubuntu kernel: [104534.804202] eth0: link down.
Apr 25 23:34:08 plui-amd64-ubuntu kernel: [104536.478149] eth0: link up.
Apr 25 23:34:10 plui-amd64-ubuntu kernel: [104539.203295] eth0: link down.
Apr 25 23:34:12 plui-amd64-ubuntu kernel: [104540.840070] eth0: link up.
Apr 25 23:34:15 plui-amd64-ubuntu kernel: [104543.391321] eth0: link down.
Apr 25 23:34:16 plui-amd64-ubuntu kernel: [104545.034121] eth0: link up.
Apr 25 23:34:57 plui-amd64-ubuntu kernel: [104585.397425] eth0: link down.
Apr 25 23:34:58 plui-amd64-ubuntu kernel: [104587.057432] eth0: link up.
Apr 25 23:35:18 plui-amd64-ubuntu kernel: [104607.266864] eth0: link down.
Apr 25 23:35:20 plui-amd64-ubuntu kernel: [104608.950673] eth0: link up.
```

I also noticed I can't connect on aMSN.  Could be a related problem?

Any idea why this is happening?

---

### Post by noii on 2009-08-10
I'm seeing the same problem. For a while the wired connection was ok after upgrading to 9.04 (maybe a month). I did notice it very occasionally drop and reconnect. 

But now it's just connecting and disconnecting every couple of seconds.

Any ideas how to debug this?

---

### Post by Iowan on 2009-08-10
I doubt it's related, but the [rfc3442]("http://ubuntuforums.org/showthread.php?t=1156441") option caused me problems.

---

### Post by noii on 2009-08-18
thanks Iowan. 

I tried editing /etc/dhcp3/dhclient.conf - commenting out the "option rfc3442" line and removed the reference in the "request" line and rebooted as you suggest. But nothing seems to have got better. It's still cycling my ethernet interface on and off every couple of seconds.

---

### Post by noii on 2009-08-18
the problems I'm having seem similar to [http://ubuntuforums.org/showthread.php?p=7794789](http://ubuntuforums.org/showthread.php?p=7794789)

but I don't think my driver is b44.

```
sudo ethtool -i eth0
driver: forcedeth
version: 0.61
firmware-version:
bus-info: 0000:00:14.0
```

```
lspci | grep -i ether
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
```

```
uname -a
Linux noiihome-media 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 22:12:12 UTC 2009 x86_64 GNU/Linux
```

---

