---
title: "ushare timeout"
date: 2008-07-25
forum: Multimedia Software
---

### Post by piratebill on 2008-07-25
I have been trying to get ushare to work with my xbox for some time now.  when I run ushare, the xbox sees it as a video source, but when I tell it to connect, the xbox just sits there and eventually times out saying there might be a firewall problem.  I am not (to my knowledge) running a fire wall on my box.  My ushare configure file looks like this:

# /etc/ushare.conf
# Edit this file with 'dpkg-reconfigure ushare'
# Configuration file for uShare

# uShare UPnP Friendly Name (default is 'uShare').
USHARE_NAME=GuiltySpark

# Interface to listen to (default is eth0).
# Ex : USHARE_IFACE=eth1
USHARE_IFACE=eth0

# Port to listen to (default is random from IANA Dynamic Ports range)
# Ex : USHARE_PORT=49200
USHARE_PORT=

# Port to listen for Telnet connections
# Ex : USHARE_TELNET_PORT=1337
USHARE_TELNET_PORT=

# Directories to be shared (space or CSV list).
# Ex: USHARE_DIR=/dir1,/dir2
USHARE_DIR=/cargo_hold/M0vie$

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
USHARE_ENABLE_XBOX=yes

# Use DLNA profile (yes/no)
# This is needed for PlayStation3 to work (among other devices)
ENABLE_DLNA=





Does anybody know what is wrong?  I am running ubuntu hardy server edition.

---

### Post by piratebill on 2008-12-09
It is solved.  Disable loopback on the router.  It prevents upnp devices on wireless from connecting to a hardlined system.

---

