---
title: "Ushare and the Xbox360 almost there"
date: 2009-06-22
forum: Multimedia Software
---

### Post by sport9155 on 2009-06-22
I have Ushare running as a daemon on ubuntu 9.04 (server), and have over come some hurdles on the way but have it running so that the Xbox360 at least see's it, but will not communicate; I keep getting told by the Xbox360 to check my connection to the PC, ie possibly a firewall issue.
So the last thing I did last night was to disable ufw and reboot the server just to clear all, but I'm still having the same issue.
Has anyone had this issue and what did you do to resolve it?
 
Thanks

---

### Post by sport9155 on 2009-06-22
Had one more look under the covers and found that not only had I said yes to xbox support but alos said yes to PS3 support, which I have now changed to "NO".  All is working fine now.

---

### Post by zbrooks on 2009-06-26
Im having the same issue.  Ushare was up and running a few weeks ago, but my xbox crapped out and I had to get it repaired.  I just got it back and now ushare is not working.

When I start ushare with "ushare -x":

```
zack@LittleBlackBox:~$ ushare -x
Interface eth0 is down.
Recheck uShare's configuration and try again !
uShare (version 1.1a), a lightweight UPnP A/V and DLNA Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See http://ushare.geexbox.org/ for updates.
bind: Address already in use
```

I tried it this way "ushare -t -x" to disable telnet

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

When I do this it shows up on my xbox but I get an error that I cant connect to it and may be a firewall issue.

I know its not the ps3 thing because here is my ushare.conf file:

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

Any ideas?

---

### Post by SirTravers on 2010-09-07
I see you haven't changed your port information so the XBOX can see your computer.

Currently yours is set as  [FONT=monospace][/FONT]USHARE_PORT=49200. Change the number to 49153
I got the information here...  [http://liamm.com/tech/how-toxbox-360-media-server-in-linux](http://liamm.com/tech/how-toxbox-360-media-server-in-linux)

Follow that and you'll be up and running in no time.

---

