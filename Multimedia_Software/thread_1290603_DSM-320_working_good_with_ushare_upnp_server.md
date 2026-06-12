---
title: "DSM-320 working good with ushare upnp server"
date: 2009-10-13
forum: Multimedia Software
---

### Post by sdowney717 on 2009-10-13
it does play vlc recorded mpg files
ushare is in synaptic

ushare.conf is in /etc/
simply run ushare with no arguments on the command line and it will use the settings in ushare.conf. 

also, if your mediaplayer DSM-320 cant update the firmware from the web, plug it directly into your cable modem, bypass the router. set it to DHCP not static. mine was now able to update the firmware.

> # /etc/ushare.conf
# Edit this file with 'dpkg-reconfigure ushare'
# Configuration file for uShare

# uShare UPnP Friendly Name (default is 'uShare').
USHARE_NAME=uShare

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
USHARE_DIR=/home/scott2/Videos

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
ENABLE_XBOX=

# Use DLNA profile (yes/no)
# This is needed for PlayStation3 to work (among other devices)
ENABLE_DLNA=


[http://buffalo.nas-central.org/wiki/Ushare_-_UPnP_Media_Server_for_Linux#Start](http://buffalo.nas-central.org/wiki/Ushare_-_UPnP_Media_Server_for_Linux#Start)
if you add new files to your shared folder, you got to stop the server and reload, then start

> scott2@scott2-desktop:~$ sudo /etc/init.d/ushare stop
 * Stopping uShare UPnP A/V & DLNA Media Server: ushare                  [ OK ] 
scott2@scott2-desktop:~$ sudo /etc/init.d/ushare status
 * Usage: /etc/init.d/ushare {start|stop|restart|reload|force-reload}
scott2@scott2-desktop:~$ sudo /etc/init.d/ushare reload
 * Reloading uShare UPnP A/V & DLNA Media Server: ushare                 [ OK ] 
scott2@scott2-desktop:~$ sudo /etc/init.d/ushare start
 * Starting uShare UPnP A/V & DLNA Media Server: ushare                  [ OK ] 
scott2@scott2-desktop:~$ 


---

