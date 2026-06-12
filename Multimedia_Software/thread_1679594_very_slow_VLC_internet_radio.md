---
title: "very slow VLC internet radio"
date: 2011-02-01
forum: Multimedia Software
---

### Post by natman on 2011-02-01
Hi,
I am using VLC to listen to a radio stream online. It works ok, but always takes ~2min to actually connect to the stream. I opened VLC up via a terminal and got the following output:
> natman@flame:~$ vlc
VLC media player 1.1.4 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x1c3b120] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Blocked: call to sigaction(17, 0x7f31ce66ab20, 0x7f31ce66aa80)
Blocked: call to setlocale(6, "")
(2031) KSharedDataCache::Private::mapSharedMemory: Opening cache "/var/tmp/kdecache-natman/icon-cache.kcache" page size is 4096
(2031) KSharedDataCache::Private::mapSharedMemory: Attached to cache, determining if it must be initialized
(2031) KSharedDataCache::Private::mapSharedMemory: Cache fully initialized -- attached to memory mapping
(2031) KSharedDataCache::Private::mapSharedMemory: 4251648 bytes available out of 10485760
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /home/natman/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
Blocked: call to setenv("_PX_CONFIG_ORDER", "", 1)
Blocked: call to setenv("_PX_CONFIG_ORDER", "", 1)
[0x1c4d590] main playlist: stopping playback
[0x20db820] access_mms access: selecting stream[0x1] audio (31 Kib/s)
[0x20db820] access_mms access: connection successful
TagLib: Could not open file live1.rte.ie/wmtencoder/radio1.wma

From "Blocked" down ( i.e sixth last line ) seems to be where vlc is staling - is there anyway for me to tell VLC to skip some step that seems to be delaying it? The stream i want is:
[http://dynamic.rte.ie/av/live/radio/radio1.asx](http://dynamic.rte.ie/av/live/radio/radio1.asx) 

Thanks:

---

### Post by andrew.46 on 2011-02-02
Is it a little faster using the direct address: *mms://live1.rte.ie/wmtencoder/radio1.wma* ?

---

