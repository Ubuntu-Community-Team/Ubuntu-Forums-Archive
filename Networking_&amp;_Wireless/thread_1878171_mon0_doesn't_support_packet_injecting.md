---
title: "mon0 doesn't support packet injecting"
date: 2011-11-09
forum: Networking &amp; Wireless
---

### Post by mafi127 on 2011-11-09
I trying to get my wifi cart to support injnection in monitor mode. In ubuntu 11.04 I used this script to get it working 

[PHP]#!/bin/bash
filedate="2011-11-08"
wget http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-${filedate}.tar.bz2
tar -jxf compat-wireless-${filedate}.tar.bz2
cd compat-wireless-${filedate}
wget http://patches.aircrack-ng.org/mac80211.compat08082009.wl_frag+ack_v1.patch
patch -p1 < mac80211.compat08082009.wl_frag+ack_v1.patch
wget http://patches.aircrack-ng.org/channel-negative-one-maxim.patch
patch ./net/wireless/chan.c channel-negative-one-maxim.patch
make
make install
make unload
modprobe iwl3945
echo "Rebooting in 10 secs......"
sleep 10
reboot[/PHP]

But now when I trying to use this script in ubuntu 11.10 then I get this errors when I' running it 

[PHP]
2011-11-09 16:47:43 (62,8 MB/s) - `channel-negative-one-maxim.patch' saved [1021/1021]

patching file ./net/wireless/chan.c
Hunk #1 succeeded at 82 (offset 33 lines).
Hunk #2 succeeded at 134 (offset 55 lines).
make: execvp: ./scripts/check_config.sh: Permission denied
make: *** [.compat_autoconf_compat-wireless-2011-10-14-1-g6dec5d8] Error 127


make: execvp: ./scripts/check_config.sh: Permission denied
make: *** [.compat_autoconf_compat-wireless-2011-10-14-1-g6dec5d8] Error 127
make: execvp: ./scripts/unload.sh: Permission denied
make: *** [unload] Error 127
Rebooting in 10 secs......
[/PHP]

Now I'm get this error whit my wifi drivers

[PHP]mon0 doesn't support packet injecting [2][/PHP]

btw yes I'm running script whit sudo bash script

Can some1 help me get this working aigan plz :/

---

### Post by mafi127 on 2011-11-09
Some1?

---

### Post by mafi127 on 2011-11-10
I'm using Intel 4965/5xxx  whit  iwlagn drivers.

---

### Post by nothingspecial on 2011-11-10
aircrack is not supported here. Closed.

---

