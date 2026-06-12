---
title: "Ushare having problems with .WMV and .MKV"
date: 2011-01-16
forum: Multimedia Software
---

### Post by JayD3e2010 on 2011-01-16
I have a Ushare server up and running in Ubuntu-Server 10.10.  So far the only video type I have been able to get working on my Xbox360 is .avi.  I am very interested in configuring it to play .wmv and .mkv videos as well, seeing as most of my library is made up of these two file-types.  After taking a look at ushare's [documentation]("http://ushare.geexbox.org/"), I found that .wmv and .mkv are both fully supported video formats; however, I can't seem to get either of them to work.  Every time I attempt to play either of those two type, I receive a message saying:  Unplayable Content:  Can't play this content because it may not be supported.  For more info, go to....

Here is my ushare.conf file:


# /etc/ushare.conf
# Edit this file with 'dpkg-reconfigure ushare'
# Configuration file for uShare

# uShare UPnP Friendly Name (default is 'uShare').
USHARE_NAME=FATMAN-VIDEOS

# Interface to listen to (default is eth0).
# Ex : USHARE_IFACE=eth1
USHARE_IFACE=ra0

# Port to listen to (default is random from IANA Dynamic Ports range)
# Ex : USHARE_PORT=49200
USHARE_PORT=49153

# Port to listen for Telnet connections
# Ex : USHARE_TELNET_PORT=1337
USHARE_TELNET_PORT=1337

# Directories to be shared (space or CSV list).
# Ex: USHARE_DIR=/dir1,/dir2
USHARE_DIR=/raid/Videos,/raid/Music/Xbox360

# Use to override what happens when iconv fails to parse a file name.
# The default uShare behaviour is to not add the entry in the media list
# This option overrides that behaviour and adds the non-iconv'ed string into
# the media list, with the assumption that the renderer will be able to
# handle it. Devices like Noxon 2 have no problem with strings being passed
# as is. (Umlauts for all!)
#
# Options are TRUE/YES/1 for override and anything else for default behaviour
USHARE_OVERRIDE_ICONV_ERR=yes

# Enable Web interface (yes/no)
USHARE_ENABLE_WEB=yes

# Enable Telnet control interface (yes/no)
USHARE_ENABLE_TELNET=no

# Use XboX 360 compatibility mode (yes/no)
USHARE_ENABLE_XBOX=yes

# Use DLNA profile (yes/no)
# This is needed for PlayStation3 to work (among other devices)
USHARE_ENABLE_DLNA=no

---

### Post by fearpi on 2011-01-23
Having the same problem here. I haven't been able to find anything online saying explicitly one way or the other whether .MKV should work.

---

### Post by fearpi on 2011-01-26
I've just downloaded and successfully run the following tool on the advice of a coworker:

[http://code.google.com/p/ps3mediaserver/](http://code.google.com/p/ps3mediaserver/)

It transcodes on-the-fly into a format the XBOX understands. Don't let the name fool you - it supports XBOX 360 in addition to PS3. I've just streamed 720p HD rips in the MKV container format successfully to mine. Little to no setup! Good luck.

---

