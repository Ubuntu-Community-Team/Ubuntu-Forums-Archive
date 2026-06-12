---
title: "uShare Issue with Ubuntu 11.04"
date: 2011-01-10
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by tk1269 on 2011-01-10
I have been using uShare for a few years now, and up until now it has worked great. A few snags here and there, but nothing I couldn't figure out, although after five years using Ubuntu, i still consider myself a noob. Now I am on a new machine, running Ubuntu 11.04 (my last one was running 9.04) and I am having trouble with uShare again. Its installed, configured, and runs just fine, but my xbox won't recognize it.

Here's the catch: the first night I set it up, after a few errors, I got it working! Watched a movie, smiled, and went to bed. Woke up the next morning, booted up the comp, fired up ushare and BAM! Nothing. I hadn't changed any settings, moved any cables, downloaded anything new, but no dice. After a little searching, I updated the .conf file to reflect a change I noticed in the IFACE. Sometimes when I boot my computer, it connects to the router on eth0, sometimes on eth1, and sometimes on eth0-eth1. I'm not sure what is up with that, but that may be a problem for another day. For right now, I just want uShare to work. Please help.

ushare.conf
# /etc/ushare.conf
# Edit this file with 'dpkg-reconfigure ushare'
# Configuration file for uShare

# uShare UPnP Friendly Name (default is 'uShare').
USHARE_NAME=Desktop

# Interface to listen to (default is eth0).
# Ex : USHARE_IFACE=eth1
USHARE_IFACE=eth0-eth1

# Port to listen to (default is random from IANA Dynamic Ports range)
# Ex : USHARE_PORT=49200
USHARE_PORT=49153

# Port to listen for Telnet connections
# Ex : USHARE_TELNET_PORT=1337
USHARE_TELNET_PORT=

# Directories to be shared (space or CSV list).
# Ex: USHARE_DIR=/dir1,/dir2
USHARE_DIR=/home/thomas

# Use to override what happens when iconv fails to parse a file name.
# The default uShare behaviour is to not add the entry in the media list
# This option overrides that behaviour and adds the non-iconv'ed string into
# the media list, with the assumption that the renderer will be able to
# handle it. Devices like Noxon 2 have no problem with strings being passed
# as is. (Umlauts for all!)
#
# Options are TRUE/YES/1 for override and anything else for default behaviour
USHARE_OVERRIDE_ICONV_ERR=

# Enable Web interface (yes/no)
ENABLE_WEB=

# Enable Telnet control interface (yes/no)
ENABLE_TELNET=

# Use XboX 360 compatibility mode (yes/no)
ENABLE_XBOX=yes

# Use DLNA profile (yes/no)
# This is needed for PlayStation3 to work (among other devices)
ENABLE_DLNA=

ifconfig
eth0-eth1 Link encap:Ethernet HWaddr 00:26:5a:84:6e:80
inet addr:192.168.1.100 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::226:5aff:fe84:6e80/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:40424 errors:0 dropped:0 overruns:0 frame:0
TX packets:28578 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:49660630 (49.6 MB) TX bytes:4339429 (4.3 MB)
Interrupt:21

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:116 errors:0 dropped:0 overruns:0 frame:0
TX packets:116 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:9768 (9.7 KB) TX bytes:9768 (9.7 KB)

Also, for more info, please look at the last two posts on this thread by tk1269:

[http://ubuntuforums.org/showthread.php?t=903204&page=2](http://ubuntuforums.org/showthread.php?t=903204&page=2)

Thanks in advance!

---

### Post by tom.swartz07 on 2011-01-10
Just so you know 11.04 is only in Alpha release- meaning there are some serious bugs that need to be ironed out.

That being said, if you could verify that this problem is NOT related to any existing Natty bugs, we might be able to help you.





Unless you REALLLY REALLY want to use an alpha release, I would suggest that you install the current version of Ubuntu, that being 10.10 Maverick Meerkat

---

### Post by mjpatey on 2011-01-10
IIRC, ushare doesn't run at startup by default.  To start it manually, type in a terminal:
 
```
 
ushare -x

```
 
...for Xbox 360 compatibility mode.  I wish I were on my Ubuntu box right now, because it could be that you have to type "ushare -x start"... can't remember!  One of those should start the server daemon.
 
HTH!
 
-Mark

---

### Post by xenoph on 2011-01-11
ushare -x is what my shortcut tells me, no additional 'start'.

---

### Post by cariboo on 2011-01-11
Is there a reason why you are using two network cards?

---

