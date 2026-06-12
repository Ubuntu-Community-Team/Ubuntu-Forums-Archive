---
title: "ushare doesnt run"
date: 2011-07-06
forum: Networking &amp; Wireless
---

### Post by androssofer on 2011-07-06
Hi, read a few similar threads but none helped... i'm trying to stream over my wireless to my xbox using ushare. but it keeps throwing up errors.

i'm running 11.04, and i'm 99% sure my xbox is fully updated...

when i run my ushare this is what i get: 

> Interface eth0 is down.
Recheck uShare's configuration and try again !
ioctl: Cannot assign requested address


and this is my config file

```
# /etc/ushare.conf
# Edit this file with 'dpkg-reconfigure ushare'
# Configuration file for uShare

# uShare UPnP Friendly Name (default is 'uShare').
USHARE_NAME=ushare

# Interface to listen to (default is eth0).
# Ex : USHARE_IFACE=eth0
USHARE_IFACE=wlan0

# Port to listen to (default is random from IANA Dynamic Ports range)
# Ex : USHARE_PORT=49200
USHARE_PORT=49200

# Port to listen for Telnet connections
# Ex : USHARE_TELNET_PORT=1337
USHARE_TELNET_PORT=

# Directories to be shared (space or CSV list).
# Ex: USHARE_DIR=/dir1,/dir2
USHARE_DIR=/home/username/Music,/home/username/Videos

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
USHARE_ENABLE_WEB=no

# Enable Telnet control interface (yes/no)
USHARE_ENABLE_TELNET=no

# Use XboX 360 compatibility mode (yes/no)
USHARE_ENABLE_XBOX=yes

# Use DLNA profile (yes/no)
# This is needed for PlayStation3 to work (among other devices)
USHARE_ENABLE_DLNA=
```

tia

---

