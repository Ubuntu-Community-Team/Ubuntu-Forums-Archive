---
title: "Mediatomb segmentation fault on import"
date: 2011-01-25
forum: Multimedia Software
---

### Post by frank.s on 2011-01-25
Hi All,

I have run into this problem that really bugs me now.

I have installed mediatomb on my Ubuntu box, and it has been working fine for a while now.

This morning I installed 'Gnome subtitles', and had to wrestle a bit with is to make i work (gstreamer-stuff).

Now all of a sudden, my good old mediatomb has begun to seg-fault on importing new videos.

I have tried the following:

run ffmpeg -i -> no errors
run ffmpegthumbnail -> no errors
disable all transcoding in config.xml -> no fun
disable thumbnails in config.xml -> no fun
switch to mysql DB - tables are created all right, but still -> no fun
total reinstall of mediatomb -> no fun
total uninstall + manual deletation of all mediatomb-related files + fresh install -> no fun

Frankly im running out of good ideas.

I suppose it has to do with some drivers or codecs outside of mediatomb, but I don't se why, since I have tried to turn off any kind of transcoding, thumbnailing etc.

If you have any ideas, please let me know

Regards - Frank

Output from mediatomb from the cmd-line:
```

MediaTomb UPnP Server version 0.12.0 - http://mediatomb.cc/

===============================================================================
Copyright 2005-2008 Gena Batsyan, Sergey Bostandzhyan, Leonhard Wimmer.
MediaTomb is free software, covered by the GNU General Public License version 2

2011-01-25 15:08:15    INFO: Loading configuration from: /home/frank/.mediatomb/config.xml
2011-01-25 15:08:15    INFO: Checking configuration...
2011-01-25 15:08:15    INFO: Setting filesystem import charset to UTF-8
2011-01-25 15:08:15    INFO: Setting metadata import charset to UTF-8
2011-01-25 15:08:15    INFO: Setting playlist charset to UTF-8
2011-01-25 15:08:15    INFO: Configuration check succeeded.
2011-01-25 15:08:15    INFO: Initialized port: 49152
2011-01-25 15:08:15    INFO: Server bound to: 192.168.1.10
2011-01-25 15:08:16    INFO: MediaTomb Web UI can be reached by following this link:
2011-01-25 15:08:16    INFO: http://192.168.1.10:49152/
Segmentation fault

```

The deg-fault comes when I click + in one of my media files in the browser. It doesn't matter which filetype it is, or where the file is located.

With -D parameter:
```

2011-01-25 19:57:30    INFO: MediaTomb Web UI can be reached by following this link:
2011-01-25 19:57:30    INFO: http://192.168.1.10:49152/
2011-01-25 19:57:30   DEBUG: [../src/server.cc:303] upnp_init(): end
2011-01-25 19:57:30   DEBUG: [../src/timer.cc:67] triggerWait(): triggerWait. - 0 subscriber(s)
2011-01-25 19:57:30   DEBUG: [../src/timer.cc:98] triggerWait(): nothing to do, sleeping...
2011-01-25 19:57:51   DEBUG: [../src/web_callbacks.cc:72] create_request_handler(): Filename: /content/interface?req_type=auth&return_type=xml&sid=c6784d3ad3d6ab8608edd10044b71c98&action=get_config, Path: (null)
2011-01-25 19:57:51   DEBUG: [../src/web_request_handler.cc:247] open(): request: /content/interface?req_type=auth&return_type=xml&sid=c6784d3ad3d6ab8608edd10044b71c98&action=get_config
2011-01-25 19:57:51   DEBUG: [../src/singleton.cc:73] registerSingleton(): registering new singleton... - 8 -> 9
2011-01-25 19:57:51   DEBUG: [../src/web_callbacks.cc:72] create_request_handler(): Filename: /content/interface?req_type=auth&return_type=xml&sid=c6784d3ad3d6ab8608edd10044b71c98&action=get_sid, Path: (null)
2011-01-25 19:57:51   DEBUG: [../src/web_request_handler.cc:247] open(): request: /content/interface?req_type=auth&return_type=xml&sid=c6784d3ad3d6ab8608edd10044b71c98&action=get_sid
2011-01-25 19:57:51   DEBUG: [../src/web/auth.cc:141] process(): checking/getting sid...
2011-01-25 19:57:51   DEBUG: [../src/timer.h:79] addTimerSubscriber(): adding subscriber...
2011-01-25 19:57:51   DEBUG: [../src/timer.cc:67] triggerWait(): triggerWait. - 1 subscriber(s)
2011-01-25 19:57:51   DEBUG: [../src/timer.cc:77] triggerWait(): sleeping...
2011-01-25 19:57:51   DEBUG: [../src/web_callbacks.cc:72] create_request_handler(): Filename: /content/interface?req_type=directories&return_type=xml&sid=560eca52d8bc67717e62914ede870aa1&parent_id=0&select_it=0, Path: (null)
2011-01-25 19:57:51   DEBUG: [../src/web_request_handler.cc:247] open(): request: /content/interface?req_type=directories&return_type=xml&sid=560eca52d8bc67717e62914ede870aa1&parent_id=0&select_it=0
2011-01-25 19:57:51   DEBUG: [../src/web_callbacks.cc:72] create_request_handler(): Filename: /content/interface?req_type=files&return_type=xml&sid=560eca52d8bc67717e62914ede870aa1&parent_id=0&start=0&count=25, Path: (null)
2011-01-25 19:57:51   DEBUG: [../src/web_request_handler.cc:247] open(): request: /content/interface?req_type=files&return_type=xml&sid=560eca52d8bc67717e62914ede870aa1&parent_id=0&start=0&count=25
2011-01-25 19:57:51   DEBUG: [../src/web_callbacks.cc:72] create_request_handler(): Filename: /content/interface?req_type=directories&return_type=xml&sid=560eca52d8bc67717e62914ede870aa1&parent_id=2f6d65646961&select_it=0, Path: (null)
2011-01-25 19:57:51   DEBUG: [../src/web_request_handler.cc:247] open(): request: /content/interface?req_type=directories&return_type=xml&sid=560eca52d8bc67717e62914ede870aa1&parent_id=2f6d65646961&select_it=0
2011-01-25 19:57:51   DEBUG: [../src/web_callbacks.cc:72] create_request_handler(): Filename: /content/interface?req_type=directories&return_type=xml&sid=560eca52d8bc67717e62914ede870aa1&parent_id=2f6d656469612f64&select_it=0, Path: (null)
2011-01-25 19:57:51   DEBUG: [../src/web_request_handler.cc:247] open(): request: /content/interface?req_type=directories&return_type=xml&sid=560eca52d8bc67717e62914ede870aa1&parent_id=2f6d656469612f64&select_it=0
2011-01-25 19:57:56   DEBUG: [../src/web_callbacks.cc:72] create_request_handler(): Filename: /content/interface?req_type=directories&return_type=xml&sid=560eca52d8bc67717e62914ede870aa1&parent_id=2f6d656469612f642f66696c6d&select_it=0, Path: (null)
2011-01-25 19:57:56   DEBUG: [../src/web_request_handler.cc:247] open(): request: /content/interface?req_type=directories&return_type=xml&sid=560eca52d8bc67717e62914ede870aa1&parent_id=2f6d656469612f642f66696c6d&select_it=0
2011-01-25 19:57:56   DEBUG: [../src/web_callbacks.cc:72] create_request_handler(): Filename: /content/interface?req_type=files&return_type=xml&sid=560eca52d8bc67717e62914ede870aa1&parent_id=2f6d656469612f642f66696c6d2f446f63746f722057686f20536572696573203120436f6d706c6574652048512045646974696f6e20783236342d4d50332d4d4b56205b616c6d61393965725d&start=0&count=25, Path: (null)
2011-01-25 19:57:56   DEBUG: [../src/web_request_handler.cc:247] open(): request: /content/interface?req_type=files&return_type=xml&sid=560eca52d8bc67717e62914ede870aa1&parent_id=2f6d656469612f642f66696c6d2f446f63746f722057686f20536572696573203120436f6d706c6574652048512045646974696f6e20783236342d4d50332d4d4b56205b616c6d61393965725d&start=0&count=25
2011-01-25 19:57:57   DEBUG: [../src/web_callbacks.cc:72] create_request_handler(): Filename: /content/interface?req_type=void&return_type=xml&sid=560eca52d8bc67717e62914ede870aa1, Path: (null)
2011-01-25 19:57:57   DEBUG: [../src/web_request_handler.cc:247] open(): request: /content/interface?req_type=void&return_type=xml&sid=560eca52d8bc67717e62914ede870aa1
2011-01-25 19:57:57   DEBUG: [../src/web_callbacks.cc:72] create_request_handler(): Filename: /content/interface?req_type=add&return_type=xml&sid=560eca52d8bc67717e62914ede870aa1&object_id=2f6d656469612f642f66696c6d2f446f63746f722057686f20536572696573203120436f6d706c6574652048512045646974696f6e20783236342d4d50332d4d4b56205b616c6d61393965725d, Path: (null)
2011-01-25 19:57:57   DEBUG: [../src/web_request_handler.cc:247] open(): request: /content/interface?req_type=add&return_type=xml&sid=560eca52d8bc67717e62914ede870aa1&object_id=2f6d656469612f642f66696c6d2f446f63746f722057686f20536572696573203120436f6d706c6574652048512045646974696f6e20783236342d4d50332d4d4b56205b616c6d61393965725d
2011-01-25 19:57:57   DEBUG: [../src/web/add.cc:53] process(): add: start
2011-01-25 19:57:57   DEBUG: [../src/web/add.cc:67] process(): add: returning
2011-01-25 19:57:57   DEBUG: [../src/content_manager.cc:2338] run(): running add file task with path /media/d/film/film.mkv recursive: 1
2011-01-25 19:57:57   DEBUG: [../src/singleton.cc:73] registerSingleton(): registering new singleton... - 9 -> 10
Segmentation fault

```

---

### Post by frank.s on 2011-01-26
Finally - a breakthrough !!!

I tried to think (harder) about what had changed in my setup since the last time Mediatomb was in a working state.

Then it struck me! Namoroka - (Firefox 3.6.14) - after I installed FF4.0 (Minefield) ???

So I tried to run mediatomb from the Minefield (Firefox 4.0) browser instead, and it - well didn't fix the problem, but it got me back up and runnung again.

Life is sweet :p

---

