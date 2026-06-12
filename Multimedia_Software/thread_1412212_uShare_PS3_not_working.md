---
title: "uShare PS3 not working"
date: 2010-02-20
forum: Multimedia Software
---

### Post by jaszczesniak on 2010-02-20
Hey all. I've tried looking around but I can't figure out what's going on here. I used uShare before and it worked without a hitch! I followed [these instructions here]("http://news.softpedia.com/news/How-to-Turn-Linux-Into-a-PS3-or-Xbox-360-Media-Server-102831.shtml") to the T. However, I recently did a reinstallation of 9.10 and followed the exact same instructions, and now I can't get uShare to come up on my PS3 (I haven't changed any settings on the PS3 or network since then, just reinstalled Ubuntu).

Side note. Using ```
ifconfig -a
``` I get lo, eth0 (my ethernet connection) and eth2 (which is my wifi card).  

Here are the contents of my config file:

```
# /etc/ushare.conf
# Edit this file with 'dpkg-reconfigure ushare'
# Configuration file for uShare

# uShare UPnP Friendly Name (default is 'uShare').
USHARE_NAME=inspiron-1420

# Interface to listen to (default is eth0).
# Ex : USHARE_IFACE=eth1
USHARE_IFACE=eth2

# Port to listen to (default is random from IANA Dynamic Ports range)
# Ex : USHARE_PORT=49200
USHARE_PORT=49200

# Port to listen for Telnet connections
# Ex : USHARE_TELNET_PORT=1337
USHARE_TELNET_PORT=

# Directories to be shared (space or CSV list).
# Ex: USHARE_DIR=/dir1,/dir2
USHARE_DIR=/home/joseph/video,/media/SignatureMini/Video

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
ENABLE_WEB=yes

# Enable Telnet control interface (yes/no)
ENABLE_TELNET=

# Use XboX 360 compatibility mode (yes/no)
ENABLE_XBOX=yes

# Use DLNA profile (yes/no)
# This is needed for PlayStation3 to work (among other devices)
ENABLE_DLNA=yes

```

Does anything seem to come to mind to anyone?

EDIT:

Forgot to mention that I'm executing uShare using: ```
gksu /etc/init.d/ushare reload
```

---

### Post by matchett808 on 2010-02-22
can u do a "ps -ax | grep ushare" and post results....

sudo /etc/init.d/ushare [start/restart/stop]

please note that restart may need to be followed by a start

---

