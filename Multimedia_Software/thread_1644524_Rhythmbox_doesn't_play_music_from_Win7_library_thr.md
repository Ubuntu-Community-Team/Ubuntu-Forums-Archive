---
title: "Rhythmbox doesn't play music from Win7 library through DLNA"
date: 2010-12-13
forum: Multimedia Software
---

### Post by Andras B. on 2010-12-13
Hello there fellow Ubuntuers!

I am requesting help with the following case.

I have a PC running Windows 7 Ultimate 64-bit. I have about 50GB of music in the Music library. I can connect from, play to, and download music to my DLNA enabled phone (Samsung Galaxy S), everything works fine.

When I start Rhythmbox on my laptop (Ubuntu 10.10), it sees my PC (appears under "Shared" in the left panel), but the tracks won't show on the list, it seems as if it fails to retreive the list of media. No matter how long I wait, nothing happens, the tracklist remains empty forever.

I have installed the "coherence" plugin from the Software Center.

I'll attach the console output rhythmbox generates when starting up, maybe it'll help.

Sidenote: it works the other way around, I can "Play to..." Rhythmbox from Windows Media Player.

Any help is appreciated. thanks.

```
andras@ANDRAS-LAPTOP:~$ rhythmbox

(rhythmbox:1979): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** Message: pygobject_register_sinkfunc is deprecated (GstObject)
WARN  coherence                   Dec 13 17:04:36  Coherence UPnP framework version 0.6.6.2 starting... (coherence/base.py:283)
WARN  webserver                   Dec 13 17:04:36  WebServer on port 39537 ready (coherence/base.py:124)
WARN  rb_coherence_plugin         Dec 13 17:04:36  Media Store available with UUID uuid:YZipvqdoQuHePZJIVkju (coherence/__init__.py:128)
WARN  rb_coherence_plugin         Dec 13 17:04:36  Media Renderer available with UUID uuid:cLOHJLKQfJERFPyrDAOh (coherence/__init__.py:162)
WARN  rb_coherence_plugin         Dec 13 17:04:36  start looking for media servers (coherence/__init__.py:165)
** (rhythmbox:1979): DEBUG: SyncDaemon already running, initializing SyncdaemonDaemon object
WARN  rb_media_store              Dec 13 17:04:36  __init__ MediaStore {'urlbase': 'http://192.168.1.104:39537/YZipvqdoQuHePZJIVkju', 'no_thread_needed': True, 'uuid': 'uuid:YZipvqdoQuHePZJIVkju', 'plugin': <CoherencePlugin object at 0xa852a7c (RBPlugin at 0xa0f2348)>, 'db': <__main__.RhythmDBTree object at 0xae2f48c (RhythmDBTree at 0xa0f8058)>, 'version': 2} (coherence/MediaStore.py:341)
WARN  rb_media_renderer           Dec 13 17:04:36  __init__ RhythmboxPlayer {'shell': <rb.Shell object at 0xa698504 (RBShell at 0xa0c6010)>, 'no_thread_needed': True, 'uuid': 'uuid:cLOHJLKQfJERFPyrDAOh', 'urlbase': 'http://192.168.1.104:39537/cLOHJLKQfJERFPyrDAOh', 'version': 2, 'rb_mediaserver': <coherence.upnp.devices.media_server.MediaServer object at 0xae5f0ec>} (coherence/MediaPlayer.py:37)
/usr/lib/pymodules/python2.6/coherence/extern/louie.py:44: UserWarning: extern.louie will soon be deprecated in favor of coherence.dispatcher.
  warnings.warn("extern.louie will soon be deprecated in favor of coherence.dispatcher.")
WARN  rb_media_store              Dec 13 17:04:36  __init__ MediaStore initialized (coherence/MediaStore.py:431)
WARN  mediaserver                 Dec 13 17:04:36  Rhythmbox on 192.168.1.104 MediaServer (<upnp_coherence.MediaStore.MediaStore object at 0xb4dcbec>) activated with YZipvqdoQuHePZJIVkju (coherence/upnp/devices/media_server.py:636)
WARN  mediarenderer               Dec 13 17:04:36  Rhythmbox on 192.168.1.104 MediaRenderer (RhythmboxPlayer'>) activated with cLOHJLKQfJERFPyrDAOh (coherence/upnp/devices/media_renderer.py:142)
** (rhythmbox:1979): DEBUG: Loading the real store page

** (rhythmbox:1979): WARNING **: Got less number of items in credentials hash table than expected!
** (rhythmbox:1979): DEBUG: navigation requested to https://one.ubuntu.com/music/store-no-token

(rhythmbox:1979): Rhythmbox-CRITICAL **: rb_property_view_set_selection: assertion `RB_IS_PROPERTY_VIEW (view)' failed

(rhythmbox:1979): Rhythmbox-CRITICAL **: rb_property_view_set_selection: assertion `RB_IS_PROPERTY_VIEW (view)' failed

(rhythmbox:1979): Rhythmbox-CRITICAL **: rb_property_view_set_selection: assertion `RB_IS_PROPERTY_VIEW (view)' failed

(rhythmbox:1979): Rhythmbox-CRITICAL **: rb_property_view_set_selection: assertion `RB_IS_PROPERTY_VIEW (view)' failed
WARN  event_protocol              Dec 13 17:04:38  response with error code '400' received upon our 'subscribe' request (coherence/upnp/core/event.py:233)
WARN  event_protocol              Dec 13 17:04:38  response with error code '400' received upon our 'subscribe' request (coherence/upnp/core/event.py:233)
** (rhythmbox:1979): DEBUG: navigation requested to http://stores.7digital.com/default.aspx?shop=436&partner=983
WARN  mr_client                   Dec 13 17:04:38  ConnectionManager not available, device not implemented properly according to the UPnP specification (coherence/upnp/devices/media_renderer_client.py:62)
WARN  event_protocol              Dec 13 17:04:38  response with error code '400' received upon our 'subscribe' request (coherence/upnp/core/event.py:233)

```Info: 192.168.1.104 is my laptop's IP address.

---

### Post by chrisolof on 2010-12-16
Same problem here... wish I could get this working!

Here's a snippet from the terminal:
```
Dec 16 16:06:48  error on Browse request with urn:schemas-upnp-org:service:ContentDirectory:1 /upnphost/udhisapi.dll?control=uuid:062d278a-7e49-438b-a840-ab0fbd3ddb99+urn:upnp-org:serviceId:ContentDirectory (coherence/upnp/core/action.py:112)
```

Saw a suggestion somewhere else about turning off password protected file sharing in Windows 7 - but this didn't solve the problem.

---

### Post by Andras B. on 2010-12-18
Tried turning off password protected sharing, no change.

Interesting fact #1: I can play music in Rhythmbox from my phone through DLNA, but not from the Windows machine

Interesting fact #2: if I play a file to Rhythmbox, using the "Play to" function on the Windows machine, some random tracks from the library appear in Rhythmbox, next to the one already playing.

---

### Post by jtfolden on 2010-12-19
This seems to be a Rhythmbox problem from what I can tell. 

If you install the Coherence plug-in for Totem it will probably work but the UI is a bit dodgy for listening to music.

---

### Post by chrisolof on 2010-12-20
Coherence plugin for totem does not do any better - same issue since both Rhythmbox & Totem are using Coherence to get the job done.  The issue seems to be related to the communications between Coherence and Windows 7 through DLNA.

On my Ubuntu 9.10 system this is what I'm getting in the terminal when attempting to browse the Windows 7 music library using Totem:
```
org.freedesktop.DBus.Python.twisted.python.failure.Failure: Failure: [Failure instance: Traceback (failure with no frames): <type 'exceptions.Exception'>: 402 - Invalid Args
]
```

---

### Post by jtfolden on 2010-12-20
Interesting, as Totem w/Coherence works fine for me - seeing both movies and music - but Rhythmbox seems to have troubles...

---

### Post by Andras B. on 2010-12-21
Just downloaded and "installed" the coherence plugin for Totem. Doesn't work for me. I see the Windows PC, I see the category tree (Music, Videos, etc), I see the subcategories too, but all are empty.

[ATTACH]179025[/ATTACH]

---

### Post by jtfolden on 2010-12-21
Hmm, for me, they are empty until I go into the "folder" and then they get populated with the data.

---

### Post by chrisolof on 2010-12-21
Well, in Ubuntu 10.04 the Totem plugin does appear to be working (see screenshot).

Pretty cool - but only plays one track then stops.  Seems like a Rhythmbox implementation would be much better - if only it worked.

---

### Post by chrisolof on 2011-02-19
Just stumbled upon a different tool that might work:
[http://djmount.sourceforge.net/](http://djmount.sourceforge.net/)

The idea:  Mount the Windows media locally, then import the shared media into Rhythmbox for playing.

Problem:  It's super slow and djmount hasn't been updated since 2006.

---

### Post by chrisolof on 2011-02-24
Decided to jump ship on this UPnP stuff and try an alternative.

My first thought was DAAP (Apple/iTunes), since it seems most Ubuntu audio apps have support for that as well.  I thought maybe having iTunes up and running on the Windows box would allow me to access my music through the Rhythmbox DAAP plugin.  But, from my research it looks like current versions of iTunes have changed something in their implementation of DAAP so that non-Apple implementations (such as a Rhythmbox plugin) will no longer work.

My next idea was Logitech Squeezebox.  Turns out it's all open source stuff, unlike Apple's proprietary DAAP.  And it works!  Finally, something that works!

Here's what I did to get it working:
On the Windows box install Squeezebox server:
[http://www.mysqueezebox.com/download](http://www.mysqueezebox.com/download)

On any Ubuntu machines install Wine (sudo apt-get install wine), then install the Windows version of SqueezePlay:
[http://wiki.slimdevices.com/index.php/Nightly_Builds](http://wiki.slimdevices.com/index.php/Nightly_Builds)

(there's a linux version of SqueezePlay, but it was a mess)

---

### Post by SuperFreak on 2012-06-13
I know this thread is really old but I wanted to thank you chrisolof for suggesting installing Squeezeplay through WINE. I had never thought of that and I have struggled with compiling Squeezeplay to work on my Ubuntu 10.10 machine(which eventually worked) but having upgraded to a new machine with 12.04 I could never get it to work as the instructions at Slimdevices forum and elsewhere were totally confusing. It is great to get it up and running on my computer again with WINE
Thanks

---

