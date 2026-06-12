---
title: "ushare issues with wmv, why?"
date: 2008-07-19
forum: Multimedia Software
---

### Post by Majin_Buu on 2008-07-19
:confused::confused::confused::confused::confused:I've been extremely happy with ushare so far, very fash buffering and no connection issues like I had with windows.

But my main issue right now is after ive watched/or is watchin a wvm movie, I can't "stop" the movie if I do, it wont resume the actual stream at a certain point. Sure I can restart the wmv but that's pretty annoying, since I want to resume my last viewing.

This "thing" happens with all of my wmv-hd movies, if I stop the stream/restart my 360 etc, it wont resume my movie (only happens with WMVHD).

Anyone have any ideas?

my ushare config

# /etc/ushare.conf
# Configuration file for uShare

# uShare UPnP Friendly Name (default is 'uShare').
USHARE_NAME=skynet

# Interface to listen to (default is eth0).
# Ex : USHARE_IFACE=eth1
USHARE_IFACE=

# Port to listen to (default is random from IANA Dynamic Ports range)
# Ex : USHARE_PORT=49200
USHARE_PORT=

# Port to listen for Telnet connections
# Ex : USHARE_TELNET_PORT=1337
USHARE_TELNET_PORT=

# Directories to be shared (space or CSV list).
# Ex: USHARE_DIR=/dir1,/dir2
USHARE_DIR=/home/greenfish/xbox360

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

:confused: :confused:

---

### Post by Majin_Buu on 2008-07-20
bump :popcorn:

---

