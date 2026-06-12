---
title: "help with ushare please!!"
date: 2009-06-27
forum: Multimedia Software
---

### Post by zbrooks on 2009-06-27
Okay heres the deal.  Ive been running ushare for a long while now without any problems.  I had to send my xbox360 out for repairs and now that it is back ushare has decided to stop working.  Hopefully someone can help diagnose whats going on for me because I feel like i have tried everything.

Usually I start ushare with "ushare -x" and everything is works perfect... But heres what I get.

```
zack@LittleBlackBox:~$ ushare -x
Interface eth0 is down.
Recheck uShare's configuration and try again !
uShare (version 1.1a), a lightweight UPnP A/V and DLNA Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See http://ushare.geexbox.org/ for updates.
bind: Address already in use

```

I was looking around the internet and found somewhere that said to try it with -t as well to disable telnet.


```
zack@LittleBlackBox:~$ ushare -t -x
Interface eth0 is down.
Recheck uShare's configuration and try again !
uShare (version 1.1a), a lightweight UPnP A/V and DLNA Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See http://ushare.geexbox.org/ for updates.
Initializing UPnP subsystem ...
Starting in XboX 360 compliant profile ...
UPnP MediaServer listening on 192.168.1.123:49201
Sending UPnP advertisement for device ...
Listening for control point connections ...
Building Metadata List ...
Looking for files in content directory : /media/stuff/Movies
Found 289 files and subdirectories.
```

So it seems like its sort of working with this, but when I get on my xbox and try to connect to the computer it says that it cant connect because of a possible firewall problem. Any advice on what to try would be greatly appreciated. Also here what my ushare.conf looks like just in case it is necessary. 

```
# /etc/ushare.conf
# Edit this file with 'dpkg-reconfigure ushare'
# Configuration file for uShare

# uShare UPnP Friendly Name (default is 'uShare').
USHARE_NAME=LittleBlackBox

# Interface to listen to (default is eth0).
# Ex : USHARE_IFACE=eth1
USHARE_IFACE=eth0

# Port to listen to (default is random from IANA Dynamic Ports range)
# Ex : USHARE_PORT=49200
USHARE_PORT=49200

# Port to listen for Telnet connections
# Ex : USHARE_TELNET_PORT=1337
USHARE_TELNET_PORT=1337

# Directories to be shared (space or CSV list).
# Ex: USHARE_DIR=/dir1,/dir2
USHARE_DIR=/media/stuff/Movies

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
ENABLE_DLNA=no

```

---

### Post by Jose Catre-Vandis on 2009-07-01
In your .conf file, try replacing

```
ENABLE_XBOX=yes
```
with
```
USHARE_ENABLE_XBOX=yes
```

---

