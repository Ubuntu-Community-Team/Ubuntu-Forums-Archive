---
title: "Rygel dlna server not working"
date: 2011-07-20
forum: Multimedia Software
---

### Post by staffann on 2011-07-20
I'm trying to set up rygel as a dlna server for my Panasonic TV set. I've already got minidlna working, but since it doesn't support transcoding there are some file that the tv set won't play. Therefore I decided to try to get rygel running with my 11.04 installation.

The problem is that neither the tv set nor the windows media player of my Win7 computer sees the rygel server. They can both see minidlna, so I don't think that there is a client problem. I also installed upnp-inspector on my server and the same thing is true there - rygel is not found but minidlna is.

My rygel confi file looks like this:

```

# Configuration file for Rygel
#
# In most cases, you would want to use the rygel-preferences UI rather than
# editing this file by hand.

# General configuration options
[general]
# Set it to 'true' if Rygel should be run as part of user's session.
enabled=true

# Set it to 'false' if you want to disable transcoding support.
enable-transcoding=true

# Set it to 'false' if you want to disable MP3 transcoding support.
enable-mp3-transcoder=true

# Set it to 'false' if you want to disable LPCM transcoding support.
enable-lpcm-transcoder=true

# Set it to 'false' if you want to disable mpeg transport stream
# (mpeg 2 video + audio) transcoding support.
enable-mp2ts-transcoder=true

# The network interface to attach rygel to. Leave it blank for dynamic
# configuration.
interface=wlan2
# The port to run HTTP server on. 0 means dynamic.
port=0

# The log level
#
# 1=critical
# 2=error
# 3=warning
# 4=message/info
# 5=debug
#
log-level=4

# Plugin specific sections
#
# Some options are generic and some are specific to each plugin.
# The generic ones are:
#
# * enabled: As the name suggests, to enable or disable the plugin.
# * title: The title of the plugin to advertise to UPnP clients. This can
#          contain the following automatically substituted keywords:
#       * @REALNAME@: The real name of the user as returned by
#                     g_get_real_name() function of glib library.
#       * @USERNAME@: The user name of the user as returned by
#                     g_get_user_name() function of glib library.
#       * @HOSTNAME@: The host name of the machine rygel is running on, as
#                     returned by g_get_host_name() function of glib library.
#
[Tracker]
enabled=false
share-pictures=true
share-videos=true
share-music=true
title=@REALNAME@'s media

[MediaExport]
enabled=true
title=@REALNAME@'s media
# List of URIs to export; if list is empty, the XDG media directries are
# exported.
uris=/mnt/2TBDisk/My Shared Folder;

[GstRenderer]
enabled=true

[ZDFMediathek]
enabled=true
# List of ids of broadcasts
rss=508

[GstLaunch]
enabled=false
launch_items=audiotestsrc;videotestsrc;videotestoverlay
audiotestsrc_title=Audiotestsrc
audiotestsrc_mime=audio/x-wav
audiotestsrc_launch=audiotestsrc ! wavenc
videotestsrc_title=Videotestsrc
videotestsrc_mime=video/mpeg
videotestsrc_launch=videotestsrc ! ffenc_mpeg2video ! mpegtsmux
videotestoverlay_title=Videotestsrc with timeoverlay 2
videotestoverlay_mime=video/mpeg
videotestoverlay_launch=videotestsrc ! timeoverlay ! ffenc_mpeg2video ! mpegtsmux


```

If I start rygel from the terminal with the maximum debug leverl, this is the output:

```

** (rygel:2736): DEBUG: rygel-user-config.vala:166: Loaded user configuration from file '/home/staffan/.config/rygel.conf'
** (rygel:2736): DEBUG: rygel-plugin-loader.vala:89: Searching for modules in folder '/usr/lib/rygel-1.0'.
** (rygel:2736): DEBUG: rygel-main.vala:124: new network context lo (127.0.0.1) available.
** (rygel:2736): DEBUG: rygel-main.vala:146: Ignoring network context lo (127.0.0.1).
** Message: New plugin 'MediaExport' available
** (rygel:2736): DEBUG: rygel-plugin-loader.vala:167: Loaded module source: '/usr/lib/rygel-1.0/librygel-media-export.so'
** (rygel:2736): DEBUG: rygel-plugin-loader.vala:167: Loaded module source: '/usr/lib/rygel-1.0/librygel-external.so'
** (rygel:2736): DEBUG: rygel-plugin-loader.vala:75: Plugin 'Tracker' disabled in user configuration; ignoring..
** (rygel:2736): DEBUG: rygel-plugin-loader.vala:167: Loaded module source: '/usr/lib/rygel-1.0/librygel-media-tracker.so'
** Message: New plugin 'ZDFMediathek' available
** (rygel:2736): DEBUG: rygel-plugin-loader.vala:167: Loaded module source: '/usr/lib/rygel-1.0/librygel-mediathek.so'
** (rygel:2736): DEBUG: rygel-plugin-loader.vala:134: Finished searching for modules in folder '/usr/lib/rygel-1.0'

```

Any ideas?

---

### Post by Capt_Scribble on 2011-07-24
Are you sure it's running? It's suppose to auto-start but mine doesn't. I have to type "rygel" into a terminal.

---

### Post by staffann on 2011-07-25
I did too. That is were I got the debug output from.

I also tried changing the conf-file and not specify a specific interface. Rygel will then find and use lo but not my wlan. UPnp-inspector will see rygel when run on the local machine, but neither my tv nor windows media player will see it. I believe that rygel not finding the wlan interface may be the key problem here.

---

### Post by zim2dive on 2011-12-17
Did you ever get this working?

I am also just trying rygel and can't get it seen by any of my UPNP clients.

---

### Post by staffann on 2011-12-17
No I never got Rygel working. I've been using minidlna and Serviio.
For me, minidlna worked the best for files there I don't need transcoding. Serviio has transcoding support and works pretty well in other aspects as well. In combination with my Panasonic Plasma TV both has some issues that has caused me to often use my laptop to play movies via hdmi (files copied to the laptop hdd).

---

### Post by zim2dive on 2011-12-31
I got it working.. not sure what I did differently...

Wasn't a smooth experience on the client-side... but that may also be the fault of my media player.

For now I may be sticking with Logitech Media Server. I may also look at Serviio, but it doesn't handle playlists yet.

and dang it, I can't seem to get a full removal on Twonky.. there is still some process running that advertises on my local network that Twonky is there and can be started.. even tho I've purged every bit of it that I can find...

---

