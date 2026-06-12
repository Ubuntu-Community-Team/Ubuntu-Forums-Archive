---
title: "Elisa will not start"
date: 2007-06-07
forum: Multimedia &amp; Video
---

### Post by Dexter Bip on 2007-06-07
Hi there, new Linux user and new forum member with a cry for help. Be gentle with me!

I'm running Feisty and trying to get Elisa to work, but to no avail. I've installed it in the recommended manner using apt-get and the installation seems to run fine.

However, upon trying to run the program it crashes out before starting up fully. Running it from terminal, I get the following output:

```
08/06/2007 03:51:40.485  INFO     Using config file : /home/lowden/.elisa/./elisa.conf

08/06/2007 03:51:40.644  INFO     Loaded the plugin 'services'

08/06/2007 03:51:40.669  INFO     Loaded the plugin 'pictures'

08/06/2007 03:51:40.733  INFO     Loaded the plugin 'dvd'

08/06/2007 03:51:40.738  INFO     Loaded the plugin 'music'

08/06/2007 03:51:40.758  INFO     Loaded the plugin 'movies'

08/06/2007 03:51:40.834  INFO     Loaded the plugin 'ipod'

08/06/2007 03:51:40.839  INFO     MetaFS plugin won't work without the media manager

08/06/2007 03:51:40.840  INFO     Un-loading meta_fs

08/06/2007 03:51:40.842  INFO     Loaded the plugin 'meta_fs'

08/06/2007 03:51:40.948  INFO     PythonDAAP not found. Check it out at http://jerakeen.org/code/PythonDaap/

08/06/2007 03:51:40.950  INFO     Un-loading daap_fs

08/06/2007 03:51:41.65   INFO     Loaded the plugin 'daap_fs'

08/06/2007 03:51:41.165  INFO     Loaded the plugin 'local_fs'

08/06/2007 03:51:41.397  INFO     Loaded the plugin 'flickr'

08/06/2007 03:51:41.407  INFO     Loaded the plugin 'vfs'

08/06/2007 03:51:41.482  INFO     Loaded the plugin 'upnp'

08/06/2007 03:51:41.485  INFO     Plugins not found : daap_fs, meta_fs

08/06/2007 03:51:41.811  INFO     Loaded the plugin 'weather'

08/06/2007 03:51:42.21   INFO     Loaded the plugin 'config'

08/06/2007 03:51:42.141  INFO     Loaded the plugin 'hal'

08/06/2007 03:51:42.145  INFO     Loaded the plugin 'upnp_server'

08/06/2007 03:51:42.331  INFO     Loaded the plugin 'web_radio'

08/06/2007 03:51:42.334  INFO     Loaded the plugin 'upnp_renderer'

08/06/2007 03:51:42.337  INFO     Loaded the plugin 'http_server'

08/06/2007 03:51:42.360  INFO     [lastfm] Adding location  'lastfm://globaltags/rock'

08/06/2007 03:51:42.425  INFO     [lastfm] Adding location  'lastfm://globaltags/rock'

08/06/2007 03:51:42.427  INFO     No data access plugin found for : lastfm://globaltags/rock

08/06/2007 03:51:42.438  INFO     [lastfm] Adding location  'lastfm://globaltags/jazz'

08/06/2007 03:51:42.440  INFO     No data access plugin found for : lastfm://globaltags/jazz

08/06/2007 03:51:42.524  INFO     [lastfm] Adding location  'lastfm://globaltags/rock'

08/06/2007 03:51:42.526  INFO     No data access plugin found for : lastfm://globaltags/rock

08/06/2007 03:51:42.527  INFO     [lastfm] Adding location  'lastfm://globaltags/jazz'

08/06/2007 03:51:42.529  INFO     No data access plugin found for : lastfm://globaltags/jazz

08/06/2007 03:51:42.534  INFO     [music] Adding location  'meta://artist:list'

08/06/2007 03:51:42.545  INFO     No data access plugin found for : meta://artist:list

08/06/2007 03:51:42.550  INFO     [music] Adding location  'meta://artist:list'

08/06/2007 03:51:42.630  INFO     No data access plugin found for : meta://artist:list

08/06/2007 03:51:42.635  INFO     [lastfm] Adding location  'lastfm://globaltags/jazz'

08/06/2007 03:51:42.651  INFO     Loaded the plugin 'lastfm'

08/06/2007 03:51:42.729  INFO     Using LIRC config file: /usr/lib/python2.4/site-packages/elisa/core/plugins/data/streamzap.lirc

elisa: could not connect to socket

elisa: No such file or directory

08/06/2007 03:51:42.731  INFO     Loaded the plugin 'lirc'

08/06/2007 03:51:42.824  INFO     Loaded the plugin 'audioscrobbler'

08/06/2007 03:51:43.81   INFO     [music] Adding location  'meta://artist:list'

08/06/2007 03:51:43.83   INFO     No data access plugin found for : meta://artist:list

08/06/2007 03:51:43.89   INFO     libgpod not found. Check out CVS snapshot at http://www.gtkpod.org/libgpod.html

08/06/2007 03:51:43.101  INFO     Un-loading ipod

08/06/2007 03:51:43.104  INFO     Un-loading web_radio

08/06/2007 03:51:43.177  INFO     Unable to initialize lirc!

08/06/2007 03:51:43.178  INFO     Un-loading lirc

08/06/2007 03:51:43.181  INFO     Please configure your Last.FM account settings

08/06/2007 03:51:43.182  INFO     Un-loading audioscrobbler

/usr/bin/python2.4: symbol lookup error: /usr/lib/pigment-0.1/libpgmrendergl1.so: undefined symbol: glXGetProcAddress

```

(in case you were wondering: yes the timestamps are real local time and, yes, it is past my bedtime)

I've rummaged around Google, here and the Elisa pages a fair bit in the hope of finding something, but to no avail. I suspect from what I've gleaned though that it's something to do with my graphics card so, for reference; I'm using an nvidia tnt2 card and the legacy nvidia drivers. I've spent the past couple of days playing about with the drivers and xorg.conf and I'm *almost* completely sure that everything there is as it should be now. There are certainly no problems with any other programs (yet).

I hope this is an appropriate place to be asking this, and any help will be much appreciated.

---

### Post by Dexter Bip on 2007-06-08
Any ideas, anyone?

---

### Post by zheepeez on 2007-06-14
look at your elisa.conf file - disable the MetaFS plugin and try again, if that doesn't work disable daap_fs, try again, and so forth. From what I've heard from Elisa users with problems (and my own) they pretty much all derive from the elisa.conf file... you could always ask a user to post theirs and see what's different.

Sorry I can't give any specific instructions - when I was having problems, I was told to head on over to the Elisa IRC channel (look it up on their trac page) and they were REALLY helpful

---

