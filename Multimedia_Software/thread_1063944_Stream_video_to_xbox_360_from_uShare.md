---
title: "Stream video to xbox 360 from uShare"
date: 2009-02-08
forum: Multimedia Software
---

### Post by Nihilism65 on 2009-02-08
I have uShare ver. 1.1a and I had it set up to stream media to my xbox 360 for all of about 20 minutes. I have no idea why but the xbox just stopped seeing it on the network. I tried uninstalling uShare and making a fresh config file but still cannot the xbox to see the server running. Has anybody had this problem or have any ideas how I can get it working again?

Or if anybody has any other method of streaming video to the xbox 360 without using wine I'm willing to give any other methods a try as well.

---

### Post by Slowspeed on 2009-02-14
> **Nihilism65 said:**
> I have uShare ver. 1.1a and I had it set up to stream media to my xbox 360 for all of about 20 minutes. I have no idea why but the xbox just stopped seeing it on the network. I tried uninstalling uShare and making a fresh config file but still cannot the xbox to see the server running. Has anybody had this problem or have any ideas how I can get it working again?

Or if anybody has any other method of streaming video to the xbox 360 without using wine I'm willing to give any other methods a try as well.

This setup worked for me and I passed it on it this thread.
[http://ubuntuforums.org/showthread.php?t=903204](http://ubuntuforums.org/showthread.php?t=903204)

I actually have the video streaming from ushare to my xbox 360.
My setup is as follows:

1. Ubuntu v.8.10 - gnome desktop
2. Ushare v 1.1a from the Ubuntu repository I just used apt to install the package. I did not compile source code like some other people were recommending.
3. xbox 360 with the latest software.

UShare.conf
I followed different instructions but after several changes it worked on the following:
my ushare.conf file:
# /etc/ushare.conf
# Edit this file with 'dpkg-reconfigure ushare'
# Configuration file for uShare

# uShare UPnP Friendly Name (default is 'uShare').
USHARE_NAME=uShare

# Interface to listen to (default is eth0).
# Ex : USHARE_IFACE=eth1
USHARE_IFACE=

# Port to listen to (default is random from IANA Dynamic Ports range)
# Ex : USHARE_PORT=49200
USHARE_PORT=49153

# Port to listen for Telnet connections
# Ex : USHARE_TELNET_PORT=1337
USHARE_TELNET_PORT=

# Directories to be shared (space or CSV list).
# Ex: USHARE_DIR=/dir1,/dir2
USHARE_DIR=/home/user/Videos,/home/user/Music

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
ENABLE_DLNA=

#EOF

As you can see I removed the ethernet interface variable.

Next. I started ushare with the following command:

ushare -x

I also verified that UFW is not loaded.

It then reported as usual that my ethernet interface was down, but it kept going and started.

Then I went and turned on my xbox and there it was listed as Ushare.
I am streaming an avi and it is working well.

---

