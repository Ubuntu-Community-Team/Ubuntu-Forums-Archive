---
title: "Help with 360 connection..."
date: 2008-12-12
forum: Multimedia Software
---

### Post by mbtigger on 2008-12-12
I have been readin all about USHARE and x360media and have been trying to get them set up on my 8.10 linux box. 

U have gone through this thread 

I think I have the ushare working on my linux box. at least when I type "ushare" at the prompt I get the following


uShare (version 1.1a-NeToU), a lightweight UPnP A/V and DLNA Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See [http://ushare.geexbox.org/](http://ushare.geexbox.org/) for updates.
Initializing UPnP subsystem ...
UPnP MediaServer listening on 192.168.1.65:49200
Sending UPnP advertisement for device ...
Listening for control point connections ...
Building Metadata List ...
Looking for files in content directory : (shared directory)
Found 107 files and subdirectories.

But when I go to the xbox 360 and tell it to test a PC connection all I get is "PC NOT LISTED". 

I don't use static IP's - I let my router do all that - so I am not sure if I can do the firewall thing or not.

Any suggestions as to why my 360 won't recognize my UPnP share?

Thanks in advance

MB

---

### Post by nigel502 on 2009-01-22
I have had the exact same issue. Have you been able to resolve it?

---

### Post by Slowspeed on 2009-02-14
Here is my ushare conf that works. Take note of the Port number change.

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

Hope this helps 
Slowspeed

---

### Post by Dodsfall on 2010-03-01
> # Use XboX 360 compatibility mode (yes/no)
ENABLE_XBOX=yes

In the configuration does not always work. (At least it didn't for me.) I had to edit the /etc/init.d/ushare file to "turn on" XBox360 compatibility.

> 
sudo gedit /etc/init.d/ushare


The add the following line [COLOR="Red"](in red)[/COLOR] near the top under the CONFIGFILE=/etc/ushare.conf line like this:

> 
CONFIGFILE=/etc/ushare.conf
[COLOR="Red"]USHARE_OPTIONS=-x[/COLOR]


Save the file. Stop and restart the daemon and you should be good to go. 

> 
sudo /etc/init.d/ushare stop


then

> 
sudo /etc/init.d/ushare start


---

