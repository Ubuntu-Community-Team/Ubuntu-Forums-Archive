---
title: "Running Rygel on Ubuntu Server 20.04"
date: 2020-09-04
forum: Multimedia Software
---

### Post by porkpiehat2 on 2020-09-04
I'm trying to set up Rygel as DLNA-server on my Ubuntu Server install. However, I cannot get Rygel configured and starting properly.
In the Rygel docs it mentions that it comes with two server plugins pre-installed, Tracker or Media Export, and it should be configured to use either of these. But Rygel does not start properly at all with either of the two enabled. I double-checked that all dependencies are properly installed.

Thanks in advance for any help!

With Media Export enabled, it stalls indefinitely on startup:
```
Rygel-Message: 21:27:07.793: Rygel v0.38.3 starting…RygelCore-Message: 21:27:07.964: New plugin “MediaExport” available
MediaExport-Message: 21:27:08.059: “file:///media/nas-public/test” harvested
MediaExport-Message: 21:27:08.070: rygel-media-export-harvesting-task.vala:309: Harvesting of file:///media/nas-public/test done in 0.020710
MediaExport-Message: 21:27:08.073: rygel-media-export-extract.vala:180: Started with descriptors 3 (in) 4 (out)
```


With Tracker enabled:
```
Rygel-Message: 21:17:16.639: Rygel v0.38.3 starting…(rygel:47746): Rygel-WARNING **: 21:17:22.124: No plugins found in 5 seconds; giving up…

```

This is my config:
```

# Configuration file for Rygel


# General configuration options
[general]


# Set it to 'false' if you want to disable transcoding support.
enable-transcoding=true


# Where video files should be saved if allow-upload is true.
# Defaults to @VIDEOS@, the standard videos folder (typically ${HOME}/Videos).
video-upload-folder=@VIDEOS@


# Where music files should be saved if allow-upload is true
# Defaults to @MUSIC@, the standard music folder (typically ${HOME}/Music).
music-upload-folder=@MUSIC@


# Where picture files should be saved if allow-upload is true
# Defaults to @PICTURES@, the standard picture folder (typically ${HOME}/Pictures).
picture-upload-folder=@PICTURES@


# Default media engine to load. If not specified, the engine directory is
# searched recursively and the first engine found is loaded.
media-engine=librygel-media-engine-gst.so


# List of network interfaces to attach rygel to. You can also use network IP or
# even ESSID for wireless networks on Linux. Leave it blank for dynamic
# configuration.
interface=wlp2s0


# The port to run HTTP server on. 0 means dynamic.
port=0


# Comma-separated list of domain:level pairs to specify log level thresholds for
# individual domains. domain could be either 'rygel', name of a plugin or '*'
# for all domains. Allowed levels are:
#
# 1=critical
# 2=error
# 3=warning
# 4=message/info
# 5=debug
log-level=*:5


# Allow upload of media files?
allow-upload=false


# Allow deletion of media folders and files?
allow-deletion=false


# Semicolon-separated list of device user-agents (or parts thereof) that need
# a downgrade in the UPnP device versions
# WARNING /!\: Only change this setting when told to do so or when you know
#              what you're doing. If you find that adding your device makes it
#              working with Rygel, please file a bug at
#              https://gitlab.gnome.org/GNOME/rygel/issues/new/?issuable_template=IOP
#              so we can include it in future releases.
#force-downgrade-for=Allegro-Software-WebClient;SEC_HHP;SEC HHP;Mediabolic-IMHTTP/1;TwoPlayer;Reciva;FDSSDP;Portable SDK for UPnP devices;Darwin


# Access controll fall-back policy if no access control provider could be
# found. Default is to true which will allow any peer to access anything.
acl-fallback-policy=true


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


# Options related to the used media backend.
# The options shown in this configuration file are specific to GStreamer.
[GstMediaEngine]


# List of active transcoders. To disable one, remove from list.
transcoders=mp3;lpcm;mp2ts;wmv;aac;avc


# Options that apply to the renderer framework in general
[Renderer]


# Default showtime in seconds to use for images in playlists if dlna:lifetime
# is not set. DLNA wants something between 5 and 15 seconds.
image-timeout = 15


[Tracker]
enabled=true
#only-export-from=@MUSIC@;@VIDEOS@;@PICTURES@;/media/nas-public/Movies
only-export-from=/media/nas-public/test
share-pictures=true
share-videos=true
share-music=true
strict-sharing=false
title=@REALNAME@'s media


[LMS]
enabled=false
title=@REALNAME@'s media on @PRETTY_HOSTNAME@


[MediaExport]
enabled=false
title=@REALNAME@'s media
# List of URIs to export. Following variables are automatically substituted by
# the appropriate XDG standard media folders by Rygel for you.
#
#       * @MUSIC@: The standard music folder (typically ${HOME}/Music).
#       * @VIDEOS@: The standard videos folder (typically ${HOME}/Videos).
#       * @PICTURES@: The standard pictures folder (typically ${HOME}/Pictures).
#
#uris=@MUSIC@;@VIDEOS@;@PICTURES@;/media/nas-public/Movies
uris=/media/nas-public/test
extract-metadata=true
monitor-changes=true
monitor-grace-timeout=5
#virtual-folders=true


[Playbin]
enabled=false
title=Audio/Video playback on @PRETTY_HOSTNAME@
#audio-sink=autoaudiosink
#video-sink=fakesink


[GstLaunch]
enabled=false
launch-items=audiotestsrc;videotestsrc;videotestoverlay
audiotestsrc-title=Audiotestsrc
audiotestsrc-mime=audio/x-wav
audiotestsrc-launch=audiotestsrc ! wavenc
videotestsrc-title=Videotestsrc
videotestsrc-mime=video/mpeg
videotestsrc-launch=videotestsrc ! avenc_mpeg2video ! mpegtsmux
videotestoverlay-title=Videotestsrc with timeoverlay 2
videotestoverlay-mime=video/mpeg
videotestoverlay-launch=videotestsrc ! timeoverlay ! avenc_mpeg2video ! mpegtsmux


[Test]
enabled=false


[ExampleServerPluginVala]
enabled=false


[ExampleServerPluginC]
enabled=false


[ExampleRendererPluginVala]
enabled=false


[ExampleRendererPluginC]
enabled=false


[MPRIS]
enabled=false


[External]
enabled=false


[Ruih]
enabled=false
title=Rygel Remote UI Server

```

---

### Post by 21Jerry on 2020-12-26
Did you ever get this running?

I am running on ubuntu server 19 (headless).  I installed rygel and it runs and shows up on my clients.  But adding anything to the Music or Video directory causes Media Export to hang, I assume, because it no long displays the console message or broadcasts as available.

With empty Music and Video directories:

```

Rygel-Message: 15:45:51.728: rygel-acl.vala:143: No ACL fallback policy found. Using “allow”
Rygel-Message: 15:45:51.729: Rygel v0.36.1 starting…
RygelCore-Message: 15:45:51.736: New plugin “MediaExport” available
MediaExport-Message: 15:45:51.891: “file:///home/jerry/Music” harvested
MediaExport-Message: 15:45:51.891: rygel-media-export-harvesting-task.vala:309: Harvesting of file:///home/jerry/Music done in 0.019684
MediaExport-Message: 15:45:51.891: “file:///home/jerry/Videos” harvested
MediaExport-Message: 15:45:51.891: rygel-media-export-harvesting-task.vala:309: Harvesting of file:///home/jerry/Videos done in 0.017371
MediaExport-Message: 15:45:51.891: “file:///home/jerry/Pictures” harvested
MediaExport-Message: 15:45:51.893: rygel-media-export-harvesting-task.vala:309: Harvesting of file:///home/jerry/Pictures done in 0.016097
MediaExport-Message: 15:45:51.911: rygel-media-export-extract.vala:180: Started with descriptors 3 (in) 4 (out)
MediaExport-Message: 15:45:51.913: rygel-media-export-extract.vala:180: Started with descriptors 3 (in) 4 (out)
MediaExport-Message: 15:45:51.915: rygel-media-export-extract.vala:180: Started with descriptors 3 (in) 4 (out)

```

If I add anything even the smallest .m4a file to the Music directory or a video to the Video directory, I get the following and it no longer broadcasts as available:

```

Rygel-Message: 15:43:29.070: rygel-acl.vala:143: No ACL fallback policy found. Using “allow”
Rygel-Message: 15:43:29.070: Rygel v0.36.1 starting…
RygelCore-Message: 15:43:29.077: New plugin “MediaExport” available
MediaExport-Message: 15:43:29.229: “file:///home/jerry/Videos” harvested
MediaExport-Message: 15:43:29.229: rygel-media-export-harvesting-task.vala:309: Harvesting of file:///home/jerry/Videos done in 0.021016
MediaExport-Message: 15:43:29.232: “file:///home/jerry/Pictures” harvested
MediaExport-Message: 15:43:29.232: rygel-media-export-harvesting-task.vala:309: Harvesting of file:///home/jerry/Pictures done in 0.021319
MediaExport-Message: 15:43:29.245: rygel-media-export-extract.vala:180: Started with descriptors 3 (in) 4 (out)
MediaExport-Message: 15:43:29.247: rygel-media-export-extract.vala:180: Started with descriptors 3 (in) 4 (out)
MediaExport-Message: 15:43:29.250: rygel-media-export-extract.vala:180: Started with descriptors 3 (in) 4 (out)

```

note the missing messages: 

[B]MediaExport-Message: 15:45:51.891: “file:///home/jerry/Music” harvested
MediaExport-Message: 15:45:51.891: rygel-media-export-harvesting-task.vala:309: Harvesting of file:///home/jerry/Music done in 0.019684[/B]

I tried disabling Media Export and installing Tracker, but Tracker requires an x11 head?  not sure, don't know a ton about linux.

All I'm trying to do is present pictures, audio and video to a Samsung TV.  I will put them all in a format it understands so I'm not worried about transcoding on the fly.

Any ideas?

Thanks

Jerry

---

### Post by porkpiehat2 on 2021-03-04
> **21Jerry said:**
> Did you ever get this running?

To this day, Rygel is a dead end for me. I tried again last night and actually stumbled upon my own topic again.
So far I'm using Jellyfin as full-on mediaserver for my photos and videos. It has an extensive webUI, lots of features and decent app, and can be controlled directly via my TV. But it is not as lightweight.

Last night I wanted to install a lightweight DLNA server for a music streamer, again no luck with Rygel. MiniDLNA seems to be the go-to solution back in the day, but it died out. Its reincarnation, ReadyMedia, seems somewhat active. I still need to try that. It has limited features, no webUI, and super lightweight.
I just installed Gerbera, based on the old MediaTomb. It has a few more features than MiniDLNA, the "webUI" is rough and is only there to manage the folders. It uses about 1/5th of the resources Jellyfin needs. But it was easy to install and it seems to be working fine.

Hopefully this answer still helps you, Jerry, or anyone else looking for a lightweight headless and supported DLNA server.

---

