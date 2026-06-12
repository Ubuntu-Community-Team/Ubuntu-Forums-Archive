---
title: "ushare configuration"
date: 2008-08-03
forum: Multimedia Software
---

### Post by WebBuddha on 2008-08-03
hi there,

I'm streaming some video and audio files with ushare to my xbox360.
If I want to play some audio files, all my video files are also listed there. Is it possible to split the directories in ushare, that my audio/video files are listed in there specified foldes?

My ushare configuration:
> # /etc/ushare.conf
# Edit this file with 'dpkg-reconfigure ushare'
# Configuration file for uShare

# uShare UPnP Friendly Name (default is 'uShare').
USHARE_NAME=uShare

# Interface to listen to (default is eth0).
# Ex : USHARE_IFACE=eth1
USHARE_IFACE=eth1

# Port to listen to (default is random from IANA Dynamic Ports range)
# Ex : USHARE_PORT=49200
USHARE_PORT=49200

# Port to listen for Telnet connections
# Ex : USHARE_TELNET_PORT=1337
USHARE_TELNET_PORT=

# Directories to be shared (space or CSV list).
# Ex: USHARE_DIR=/dir1,/dir2
USHARE_DIR=/media/Video,/media/Mp3z

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
ENABLE_TELNET=no

# Use XboX 360 compatibility mode (yes/no)
USHARE_ENABLE_XBOX=yes

# Use DLNA profile (yes/no)
# This is needed for PlayStation3 to work (among other devices)
ENABLE_DLNA=no

Thanks in advance
WB

---

### Post by WebBuddha on 2008-08-05
no one here who can help me to solve my issue?

Regards
WebBuddha

---

### Post by WebBuddha on 2008-08-08
*push*

---

### Post by Joshman5K on 2009-02-15
My advice would be to share /media/, and since the two folders you wanted to share were inside of it, you should be fine.

If this was a similar problem but the two folders you wanted to share were not in the same parent folder, i would create another folder and place alias of the desired folders into your new folder.

---

