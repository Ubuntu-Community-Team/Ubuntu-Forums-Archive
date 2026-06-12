---
title: "Xbox 360 and ushare"
date: 2011-09-09
forum: Multimedia Software
---

### Post by davidy0 on 2011-09-09
Hey!

Having some trouble trying to stream to an Xbox 360 via UShare.

Linux.2.6.35-30 Generic, Ubuntu 10.10. KDE 4.5.5, Ralink 2561 Wireless Card trying to stream to an arcade over Wlan0 which is connected to a Huawei Echolife HG521 (THe router talktalk sent out sadly). I also had this problem on Windows 7 32Bit. The ushare .conf file currently looks like:
[SIZE=1]
# /etc/ushare.conf
# Edit this file with 'dpkg-reconfigure ushare'
# Configuration file for uShare

# uShare UPnP Friendly Name (default is 'uShare').
USHARE_NAME=dave_deskderp

# Interface to listen to (default is eth0).
# Ex : USHARE_IFACE=eth1
USHARE_IFACE=wlan0

# Port to listen to (default is random from IANA Dynamic Ports range)
# Ex : USHARE_PORT=49200
USHARE_PORT=49200

# Port to listen for Telnet connections
# Ex : USHARE_TELNET_PORT=1337
USHARE_TELNET_PORT=

# Directories to be shared (space or CSV list).
# Ex: USHARE_DIR=/dir1,/dir2
USHARE_DIR=/media/disk/Movies

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
USHARE_ENABLE_WEB=yes

# Enable Telnet control interface (yes/no)
USHARE_ENABLE_TELNET=no

# Use XboX 360 compatibility mode (yes/no)
USHARE_ENABLE_XBOX=yes

# Use DLNA profile (yes/no)
# This is needed for PlayStation3 to work (among other devices)
USHARE_ENABLE_DLNA=no
[/SIZE]
And I can access the Ushare information page by going to [http://localhost:49200/web/ushare.html](http://localhost:49200/web/ushare.html), but why doesn't my xbox pick it up? UPNP Is enabled in the router settings and I never had this problem before.

---

### Post by tehchibipanda on 2011-09-09
Greetings, Davidy0! I have had a similar problem with uShare; I now have a firewall issue which is something I am slowly (but surely) working on. When it comes to this issue, with the xbox not seeing your Ubuntu machine. Have you gone to "My Videos" or whichever you are trying to share before starting uShare? 

EG: Power on xbox. Then run 

```
ushare -x
```

to run in xbox compatibility mode; 

When that happens, can you post the results from terminal in here? 

Also, I think the port should be 49153 in your ushare.conf

---

