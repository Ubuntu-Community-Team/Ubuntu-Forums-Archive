---
title: "Playback on XboX 360"
date: 2008-02-13
forum: Multimedia &amp; Video
---

### Post by Hamm on 2008-02-13
I want to rip my DVD collection to have it playback on my XboX 360. I have some .avi files saved on FreeNAS and served by the uPnP media server setup, That works great. Now I want to take my collection and rip it to work the same way. I have been trying to use Acidrip, but I have had spotty success. Do I need to have the settings a certain way or is there a better software package for this? 

Thanks in advance

---

### Post by notwen on 2008-02-13
Install [dvdrip]("http://exit1.org/dvdrip/") using the following command:

```
sudo apt-get install dvdrip
```

dvdrip can rip DVDs straight to XviD(DivX alternative) .avi format.  You will likely be missing some needed libraries in order for dvdrip to work, once dvdrip is open simply Click Debug--->Check Dependencies and let it download any additional files it needs.  I use this to rip DVDs for the exact same reason, streaming xvids to my 360.   Hope this helps. =]

---

### Post by Mykle87 on 2008-02-16
> **notwen said:**
>  I use this to rip DVDs for the exact same reason, streaming xvids to my 360.   Hope this helps. =]

Is streaming to xbox 360 built right into Ubuntu?

---

### Post by notwen on 2008-02-18
You'll need to setup a uPnP server on your Linux box.  I personally use [uShare]("http://ushare.geexbox.org/").

---

### Post by Mykle87 on 2008-02-19
> **notwen said:**
> You'll need to setup a uPnP server on your Linux box.  I personally use [uShare]("http://ushare.geexbox.org/").

Was it easy to set up?

---

### Post by notwen on 2008-02-20
Pretty easy, you're installing three packages, [ushare]("http://ushare.geexbox.org/"), upnp( use this command to install: **sudo apt-get install libupnp-dev** ) and[libdlna]("http://libdlna.geexbox.org/").  Both deb files can be installed using on each specific page linked in my previous sentence(upnp and libdlna first, then ushare). =]

Then you can refer to this [thread]("http://ubuntuforums.org/showthread.php?t=631213").  Basically after you install the 3 above packages, you'll need to edit the default uShare config:

```
sudo gedit /etc/ushare.conf
```

Should look something like this below(taken from a sample found here on the forums):

```
# /etc/ushare.conf
# Edit this file with 'dpkg-reconfigure ushare'
# Configuration file for uShare

# uShare UPnP Friendly Name (default is 'uShare').
USHARE_NAME=uShare

# Interface to listen to (default is eth0).
# Ex : USHARE_IFACE=eth1
USHARE_IFACE=wlan0

# Port to listen to (default is random from IANA Dynamic Ports range)
# Ex : USHARE_PORT=49200
USHARE_PORT=

# Port to listen for Telnet connections
# Ex : USHARE_TELNET_PORT=1337
#USHARE_TELNET_PORT=

# Directories to be shared (space or CSV list).
# Ex: USHARE_DIR=/dir1,/dir2
USHARE_DIR=/home/nick/Videos,/home/nick/Music

# Use to override what happens when iconv fails to parse a file name.
# The default uShare behaviour is to not add the entry in the media list
# This option overrides that behaviour and adds the non-iconv'ed string into
# the media list, with the assumption that the renderer will be able to
# handle it. Devices like Noxon 2 have no problem with strings being passed
# as is. (Umlauts for all!)
# 
# Options are TRUE/YES/1 for override and anything else for default behaviour
#USHARE_OVERRIDE_ICONV_ERR=

# Enable Web interface (yes/no)
#USHARE_ENABLE_WEB=
# Enable Telnet control interface (yes/no)
#USHARE_ENABLE_TELNET=

# Use XboX 360 compatibility mode (yes/no)
USHARE_ENABLE_XBOX=yes

# Use DLNA profile (yes/no)
# This is needed for PlayStation3 to work (among other devices)
#USHARE_ENABLE_DLNA=
```

You should only need to modify the 3 following lines(change according to your system):
Specify your active interface
```
USHARE_IFACE=wlan0
```
Specify the folder containing media you want to share
```
USHARE_DIR=/home/user/media
```
Enable xbox abilities in uShare
```
USHARE_ENABLE_XBOX=yes
```

Post back if you have any questions and/or issues. =]

---EDIT---
Oh yeah, use this command to start uShare:

```
ushare -x
```

---

### Post by Mykle87 on 2008-02-20
Cool. Seems simple enough. Thanks.

---

### Post by GooblyWoobly on 2008-02-27
What is the best DVDRIP configuration for Xbox360. If I use the default configuration for DVD->XVid, I get black bars all around. How can I get a 16:9 full screen DVD?

---

### Post by Mykle87 on 2008-02-27
> **GooblyWoobly said:**
> What is the best DVDRIP configuration for Xbox360. If I use the default configuration for DVD->XVid, I get black bars all around. How can I get a 16:9 full screen DVD?

What program are you using to rip DVD?

---

### Post by GooblyWoobly on 2008-02-27
> **Mykle87 said:**
> What program are you using to rip DVD?

I'm using dvd::rip.

---

### Post by Mykle87 on 2008-02-27
> **GooblyWoobly said:**
> I'm using dvd::rip.

Maybe you can try K9Copy. You might have better results.

---

