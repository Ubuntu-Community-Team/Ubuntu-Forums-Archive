---
title: "Ushare not seeing HD mkv video files"
date: 2010-12-31
forum: Multimedia Software
---

### Post by sir_robert007 on 2010-12-31
I have a Samsung BD-6800 blu-ray player that i want to stream HD mkv files to from my pc. I made sure DLNA was enabled in the /etc/ushare.conf file. The blu-ray player sees my pc perfectly and i can navigate to the folders where the videos are stored, however when i select a folder with videos in it all that is shown is an option called "upper folder" which takes me back to the root directory. The videos are nowhere to be found. I checked on the Ushare web site to see if mkv files are supported which they are.

Here is what my /etc/ushare.conf looks like if this helps. 

```
# /etc/ushare.conf
# Edit this file with 'dpkg-reconfigure ushare'
# Configuration file for uShare

# uShare UPnP Friendly Name (default is 'uShare').
USHARE_NAME=uShare

# Interface to listen to (default is eth0).
# Ex : USHARE_IFACE=eth1
USHARE_IFACE=eth0

# Port to listen to (default is random from IANA Dynamic Ports range)
# Ex : USHARE_PORT=49200
USHARE_PORT=49200

# Port to listen for Telnet connections
# Ex : USHARE_TELNET_PORT=1337
USHARE_TELNET_PORT=

# Directories to be shared (space or CSV list).
# Ex: USHARE_DIR=/dir1,/dir2
USHARE_DIR=/home/robert/Videos/network_share

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
USHARE_ENABLE_WEB=

# Enable Telnet control interface (yes/no)
USHARE_ENABLE_TELNET=

# Use XboX 360 compatibility mode (yes/no)
USHARE_ENABLE_XBOX=yes

# Use DLNA profile (yes/no)
# This is needed for PlayStation3 to work (among other devices)
USHARE_ENABLE_DLNA=yes

```

---

### Post by sir_robert007 on 2011-01-01
anyone know how to solve this?

---

### Post by sir_robert007 on 2011-01-05
still waiting for a reply

---

### Post by sir_robert007 on 2011-01-10
still no reply

---

### Post by dpiddyTx on 2011-09-09
bump

I have the same problem with mkv files.

---

