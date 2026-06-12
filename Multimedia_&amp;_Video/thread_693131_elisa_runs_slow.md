---
title: "elisa runs slow"
date: 2008-02-10
forum: Multimedia &amp; Video
---

### Post by peterson2k4 on 2008-02-10
Elisa runs really slow.  I can navigate the main menu but it is choppy.  when I go any deeper the program greys out and the gives me the option of force quiting

When I run it through terminal it say the following

> 
paul@paul-desktop:~$ elisa
WARN  MainThread      comp_hal_service            Feb 10 17:22:47  org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.Hal was not provided by any .service files (elisa/plugins/good/hal/hal_service.py:91)
WARN  MainThread      service_manager             Feb 10 17:22:47  Component hal_service failed to initialize: HAL is not installed or might not be running. (elisa/core/manager.py:95)
elisa: could not connect to socket
elisa: No such file or directory
WARN  MainThread      interface_controller        Feb 10 17:22:49  Component lirc_input failed to initialize: Unable to initialize lirc! (elisa/core/interface_controller.py:324)
WARN  MainThread      comp_pigment_context        Feb 10 17:22:49  Compiz detected, trying to hide all other windows. (elisa/plugins/good/pigment/pigment_context.py:217)
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
WARN  MainThread      twisted                     Feb 10 17:22:51  A twisted traceback occurred. (twisted/internet/base.py:535)

Twisted traceback:
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py", line 175, in run
    self.__run()
  File "/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py", line 114, in wrapper
    return real_cb(real_s, condition)
  File "/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py", line 207, in callback
    self.simulate() # fire Twisted timers
  File "/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py", line 216, in simulate
    self.runUntilCurrent()
--- <exception caught here> ---
  File "/usr/lib/python2.5/site-packages/twisted/internet/base.py", line 533, in runUntilCurrent
    f(*a, **kw)
  File "/usr/lib/python2.5/site-packages/elisa/core/bus/bus.py", line 178, in _dispatch
    callback(message, sender)
  File "/usr/lib/python2.5/site-packages/elisa/plugins/good/hal/hal_service.py", line 108, in _components_loaded
    self.detect_coldplugged()
  File "/usr/lib/python2.5/site-packages/elisa/plugins/good/hal/hal_service.py", line 121, in detect_coldplugged
    udis = self.hal_iface.FindDeviceByCapability('volume')
exceptions.AttributeError: 'HalService' object has no attribute 'hal_iface'

WARN  MainThread      twisted                     Feb 10 17:23:00  A twisted traceback occurred. (twisted/spread/pb.py:910)

Twisted traceback:
Traceback (most recent call last):
Failure: exceptions.Exception: Could not determine type of stream.: gsttypefindelement.c(735): gst_type_find_element_activate (): /pipeline0/typefindelement0

WARN  MainThread      metadata_manager            Feb 10 17:23:00  failure using metadata provider gst_metadata_client: Traceback (failure with no frames): <type 'exceptions.Exception'>:  (elisa/core/metadata_manager.py:91)
WARN  MainThread      twisted                     Feb 10 17:23:01  A twisted traceback occurred. (twisted/spread/pb.py:910)

Twisted traceback:
Traceback (most recent call last):
Failure: exceptions.Exception: Could not determine type of stream.: gsttypefindelement.c(735): gst_type_find_element_activate (): /pipeline2/typefindelement3

WARN  MainThread      metadata_manager            Feb 10 17:23:01  failure using metadata provider gst_metadata_client: Traceback (failure with no frames): <type 'exceptions.Exception'>:  (elisa/core/metadata_manager.py:91)
WARN  MainThread      twisted                     Feb 10 17:23:05  A twisted traceback occurred. (twisted/spread/pb.py:910)

Twisted traceback:
Traceback (most recent call last):
Failure: exceptions.Exception: Could not determine type of stream.: gsttypefindelement.c(735): gst_type_find_element_activate (): /pipeline8/typefindelement14

WARN  MainThread      metadata_manager            Feb 10 17:23:05  failure using metadata provider gst_metadata_client: Traceback (failure with no frames): <type 'exceptions.Exception'>:  (elisa/core/metadata_manager.py:91)
WARN  MainThread      twisted                     Feb 10 17:23:05  A twisted traceback occurred. (twisted/spread/pb.py:910)

Twisted traceback:
Traceback (most recent call last):
Failure: exceptions.Exception: Could not determine type of stream.: gsttypefindelement.c(735): gst_type_find_element_activate (): /pipeline9/typefindelement15

WARN  MainThread      metadata_manager            Feb 10 17:23:05  failure using metadata provider gst_metadata_client: Traceback (failure with no frames): <type 'exceptions.Exception'>:  (elisa/core/metadata_manager.py:91)
WARN  MainThread      twisted                     Feb 10 17:23:06  A twisted traceback occurred. (twisted/spread/pb.py:910)

Twisted traceback:
Traceback (most recent call last):
Failure: exceptions.Exception: Could not determine type of stream.: gsttypefindelement.c(735): gst_type_find_element_activate (): /pipeline10/typefindelement16

WARN  MainThread      metadata_manager            Feb 10 17:23:06  failure using metadata provider gst_metadata_client: Traceback (failure with no frames): <type 'exceptions.Exception'>:  (elisa/core/metadata_manager.py:91)
WARN  MainThread      twisted                     Feb 10 17:23:06  A twisted traceback occurred. (twisted/spread/pb.py:910)

Twisted traceback:
Traceback (most recent call last):
Failure: exceptions.Exception: Could not determine type of stream.: gsttypefindelement.c(735): gst_type_find_element_activate (): /pipeline11/typefindelement17

WARN  MainThread      metadata_manager            Feb 10 17:23:06  failure using metadata provider gst_metadata_client: Traceback (failure with no frames): <type 'exceptions.Exception'>:  (elisa/core/metadata_manager.py:91)
WARN  MainThread      twisted                     Feb 10 17:23:06  A twisted traceback occurred. (twisted/spread/pb.py:910)

Twisted traceback:
Traceback (most recent call last):
Failure: exceptions.Exception: Could not determine type of stream.: gsttypefindelement.c(735): gst_type_find_element_activate (): /pipeline12/typefindelement18

WARN  MainThread      metadata_manager            Feb 10 17:23:06  failure using metadata provider gst_metadata_client: Traceback (failure with no frames): <type 'exceptions.Exception'>:  (elisa/core/metadata_manager.py:91)
WARN  MainThread      twisted                     Feb 10 17:23:07  A twisted traceback occurred. (twisted/spread/pb.py:910)

Twisted traceback:
Traceback (most recent call last):
Failure: exceptions.Exception: Could not determine type of stream.: gsttypefindelement.c(735): gst_type_find_element_activate (): /pipeline13/typefindelement19

WARN  MainThread      metadata_manager            Feb 10 17:23:07  failure using metadata provider gst_metadata_client: Traceback (failure with no frames): <type 'exceptions.Exception'>:  (elisa/core/metadata_manager.py:91)
WARN  MainThread      twisted                     Feb 10 17:23:07  A twisted traceback occurred. (twisted/spread/pb.py:910)

Twisted traceback:
Traceback (most recent call last):
Failure: exceptions.Exception: Could not determine type of stream.: gsttypefindelement.c(735): gst_type_find_element_activate (): /pipeline14/typefindelement20

WARN  MainThread      metadata_manager            Feb 10 17:23:07  failure using metadata provider gst_metadata_client: Traceback (failure with no frames): <type 'exceptions.Exception'>:  (elisa/core/metadata_manager.py:91)
WARN  MainThread      twisted                     Feb 10 17:23:08  A twisted traceback occurred. (twisted/spread/pb.py:910)

Twisted traceback:
Traceback (most recent call last):
Failure: exceptions.Exception: Could not determine type of stream.: gsttypefindelement.c(735): gst_type_find_element_activate (): /pipeline16/typefindelement23

WARN  MainThread      metadata_manager            Feb 10 17:23:08  failure using metadata provider gst_metadata_client: Traceback (failure with no frames): <type 'exceptions.Exception'>:  (elisa/core/metadata_manager.py:91)
WARN  MainThread      twisted                     Feb 10 17:23:08  A twisted traceback occurred. (twisted/spread/pb.py:910)

Twisted traceback:
Traceback (most recent call last):
Failure: exceptions.Exception: Could not determine type of stream.: gsttypefindelement.c(735): gst_type_find_element_activate (): /pipeline18/typefindelement26

WARN  MainThread      metadata_manager            Feb 10 17:23:08  failure using metadata provider gst_metadata_client: Traceback (failure with no frames): <type 'exceptions.Exception'>:  (elisa/core/metadata_manager.py:91)
WARN  MainThread      twisted                     Feb 10 17:23:09  A twisted traceback occurred. (twisted/spread/pb.py:910)

Twisted traceback:
Traceback (most recent call last):
Failure: exceptions.Exception: Could not determine type of stream.: gsttypefindelement.c(735): gst_type_find_element_activate (): /pipeline20/typefindelement29

WARN  MainThread      metadata_manager            Feb 10 17:23:09  failure using metadata provider gst_metadata_client: Traceback (failure with no frames): <type 'exceptions.Exception'>:  (elisa/core/metadata_manager.py:91)
WARN  MainThread      twisted                     Feb 10 17:23:09  A twisted traceback occurred. (twisted/spread/pb.py:910)

Twisted traceback:
Traceback (most recent call last):
Failure: exceptions.Exception: Could not determine type of stream.: gsttypefindelement.c(735): gst_type_find_element_activate (): /pipeline21/typefindelement30

WARN  MainThread      metadata_manager            Feb 10 17:23:10  failure using metadata provider gst_metadata_client: Traceback (failure with no frames): <type 'exceptions.Exception'>:  (elisa/core/metadata_manager.py:91)
WARN  MainThread      twisted                     Feb 10 17:23:10  A twisted traceback occurred. (twisted/spread/pb.py:910)

Twisted traceback:
Traceback (most recent call last):
Failure: exceptions.Exception: Could not determine type of stream.: gsttypefindelement.c(735): gst_type_find_element_activate (): /pipeline23/typefindelement33

WARN  MainThread      metadata_manager            Feb 10 17:23:10  failure using metadata provider gst_metadata_client: Traceback (failure with no frames): <type 'exceptions.Exception'>:  (elisa/core/metadata_manager.py:91)
WARN  MainThread      twisted                     Feb 10 17:23:11  A twisted traceback occurred. (twisted/spread/pb.py:910)

Twisted traceback:
Traceback (most recent call last):
Failure: exceptions.Exception: Could not determine type of stream.: gsttypefindelement.c(735): gst_type_find_element_activate (): /pipeline24/typefindelement34

WARN  MainThread      metadata_manager            Feb 10 17:23:11  failure using metadata provider gst_metadata_client: Traceback (failure with no frames): <type 'exceptions.Exception'>:  (elisa/core/metadata_manager.py:91)
WARN  MainThread      twisted                     Feb 10 17:23:12  A twisted traceback occurred. (twisted/spread/pb.py:910)

Twisted traceback:
Traceback (most recent call last):
Failure: exceptions.Exception: Could not determine type of stream.: gsttypefindelement.c(735): gst_type_find_element_activate (): /pipeline26/typefindelement37

WARN  MainThread      metadata_manager            Feb 10 17:23:12  failure using metadata provider gst_metadata_client: Traceback (failure with no frames): <type 'exceptions.Exception'>:  (elisa/core/metadata_manager.py:91)
A problem occurred in Elisa.
/tmp/elisa_VNrJz1.txt contains the description of this error.
A problem occurred in Elisa.
/tmp/elisa_IvuoiI.txt contains the description of this error.
WARN  MainThread      twisted                     Feb 10 17:23:15  A twisted traceback occurred. (twisted/spread/pb.py:910)

Twisted traceback:
Traceback (most recent call last):
Failure: exceptions.Exception: Could not determine type of stream.: gsttypefindelement.c(735): gst_type_find_element_activate (): /pipeline28/typefindelement40

WARN  MainThread      metadata_manager            Feb 10 17:23:15  failure using metadata provider gst_metadata_client: Traceback (failure with no frames): <type 'exceptions.Exception'>:  (elisa/core/metadata_manager.py:91)
WARN  MainThread      twisted                     Feb 10 17:23:16  A twisted traceback occurred. (twisted/spread/pb.py:910)

Twisted traceback:
Traceback (most recent call last):
Failure: exceptions.Exception: Could not determine type of stream.: gsttypefindelement.c(735): gst_type_find_element_activate (): /pipeline30/typefindelement43

WARN  MainThread      metadata_manager            Feb 10 17:23:16  failure using metadata provider gst_metadata_client: Traceback (failure with no frames): <type 'exceptions.Exception'>:  (elisa/core/metadata_manager.py:91)
WARN  MainThread      twisted                     Feb 10 17:23:16  A twisted traceback occurred. (twisted/spread/pb.py:910)

Twisted traceback:
Traceback (most recent call last):
Failure: exceptions.Exception: Could not determine type of stream.: gsttypefindelement.c(735): gst_type_find_element_activate (): /pipeline31/typefindelement44

WARN  MainThread      metadata_manager            Feb 10 17:23:16  failure using metadata provider gst_metadata_client: Traceback (failure with no frames): <type 'exceptions.Exception'>:  (elisa/core/metadata_manager.py:91)
WARN  MainThread      twisted                     Feb 10 17:23:17  A twisted traceback occurred. (twisted/spread/pb.py:910)

Twisted traceback:
Traceback (most recent call last):
Failure: exceptions.Exception: Could not determine type of stream.: gsttypefindelement.c(735): gst_type_find_element_activate (): /pipeline33/typefindelement47

WARN  MainThread      metadata_manager            Feb 10 17:23:17  failure using metadata provider gst_metadata_client: Traceback (failure with no frames): <type 'exceptions.Exception'>:  (elisa/core/metadata_manager.py:91)
WARN  MainThread      twisted                     Feb 10 17:23:18  A twisted traceback occurred. (twisted/spread/pb.py:910)

Twisted traceback:
Traceback (most recent call last):
Failure: exceptions.Exception: Could not determine type of stream.: gsttypefindelement.c(735): gst_type_find_element_activate (): /pipeline34/typefindelement48

WARN  MainThread      metadata_manager            Feb 10 17:23:18  failure using metadata provider gst_metadata_client: Traceback (failure with no frames): <type 'exceptions.Exception'>:  (elisa/core/metadata_manager.py:91)
WARN  MainThread      twisted                     Feb 10 17:23:18  A twisted traceback occurred. (twisted/spread/pb.py:910)

Twisted traceback:
Traceback (most recent call last):
Failure: exceptions.Exception: Could not determine type of stream.: gsttypefindelement.c(735): gst_type_find_element_activate (): /pipeline37/typefindelement53

WARN  MainThread      metadata_manager            Feb 10 17:23:18  failure using metadata provider gst_metadata_client: Traceback (failure with no frames): <type 'exceptions.Exception'>:  (elisa/core/metadata_manager.py:91)
WARN  MainThread      twisted                     Feb 10 17:23:18  A twisted traceback occurred. (twisted/spread/pb.py:910)

Twisted traceback:
Traceback (most recent call last):
Failure: exceptions.Exception: Could not determine type of stream.: gsttypefindelement.c(735): gst_type_find_element_activate (): /pipeline38/typefindelement54

WARN  MainThread      metadata_manager            Feb 10 17:23:18  failure using metadata provider gst_metadata_client: Traceback (failure with no frames): <type 'exceptions.Exception'>:  (elisa/core/metadata_manager.py:91)
WARN  MainThread      twisted                     Feb 10 17:23:19  A twisted traceback occurred. (twisted/spread/pb.py:910)

Twisted traceback:
Traceback (most recent call last):
Failure: exceptions.Exception: Could not determine type of stream.: gsttypefindelement.c(735): gst_type_find_element_activate (): /pipeline39/typefindelement55

WARN  MainThread      metadata_manager            Feb 10 17:23:19  failure using metadata provider gst_metadata_client: Traceback (failure with no frames): <type 'exceptions.Exception'>:  (elisa/core/metadata_manager.py:91)
WARN  MainThread      config                      Feb 10 17:23:22  [Errno 13] Permission denied: u'/usr/lib/python2.5/site-packages/elisa/plugins/bad/raval_frontend/tango_theme/tango_theme.conf' (elisa/core/config.py:195)
WARN  MainThread      twisted                     Feb 10 17:23:23  A twisted traceback occurred. (twisted/internet/base.py:563)

Twisted traceback:
Traceback (most recent call last):
  File "/usr/bin/elisa", line 8, in <module>
    load_entry_point('elisa==0.3.3', 'gui_scripts', 'elisa')()
  File "/usr/lib/python2.5/site-packages/elisa/core/application.py", line 512, in main
    reactor.run()
  File "/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py", line 175, in run
    self.__run()
  File "/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py", line 216, in simulate
    self.runUntilCurrent()
--- <exception caught here> ---
  File "/usr/lib/python2.5/site-packages/twisted/internet/base.py", line 561, in runUntilCurrent
    call.func(*call.args, **call.kw)
  File "/usr/lib/python2.5/site-packages/elisa/plugins/good/pigment/pigment_context.py", line 301, in _hide_cursor
    self.viewport_handle.cursor = pgm.VIEWPORT_NONE
exceptions.AttributeError: 'NoneType' object has no attribute 'cursor'

WARN  MainThread      twisted                     Feb 10 17:23:23  A twisted traceback occurred. (twisted/internet/base.py:563)

Twisted traceback:
Traceback (most recent call last):
  File "/usr/bin/elisa", line 8, in <module>
    load_entry_point('elisa==0.3.3', 'gui_scripts', 'elisa')()
  File "/usr/lib/python2.5/site-packages/elisa/core/application.py", line 512, in main
    reactor.run()
  File "/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py", line 175, in run
    self.__run()
  File "/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py", line 216, in simulate
    self.runUntilCurrent()
--- <exception caught here> ---
  File "/usr/lib/python2.5/site-packages/twisted/internet/base.py", line 561, in runUntilCurrent
    call.func(*call.args, **call.kw)
  File "/usr/lib/python2.5/site-packages/elisa/plugins/good/pigment/pigment_context.py", line 270, in _resize_canvas
    if self.viewport_size != self.viewport_handle.size:
exceptions.AttributeError: 'NoneType' object has no attribute 'size'


my specs are as follows

AMD64 | ATI xpress 200m | 512MBx2 ram

---

### Post by peterson2k4 on 2008-02-14
bump

---

### Post by Angus77 on 2008-02-20
I noticed 0.3.2 runs a lot more smoothly than 0.3.3.  Maybe a downgrade is in order?

---

### Post by granjerox on 2008-02-22
Here the same. Same error, same log. I'm running Gutsy, compiz fusion and XGL. I'm not able to reach albums screen, it slow down my computer.

How can I downgrade to 0.3.2, i've tried to download the old deb and install it, but then it replay with a backend/frontend error and doesn't run.

---

### Post by granjerox on 2008-02-23
I've discovered why it ran so slow. It was because I was running XGL-server, same problem with googleearth ....

---

### Post by andrewsomething on 2008-02-25
Any work arounds for running Elisa under XGL?

---

### Post by granjerox on 2008-02-25
I've just updated to Hardy Heron alpha 5 and all worked like a sharm. I have ati x1400 with 1680x1050 display. The driver was installed by the restricted hardware manager but it failed to configure Xorg.conf. After the first boot the graphic xorg configuration tool showed up and configured the xorg. With two fails, I had to add my resolution and a section for my usb mouse.

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg648244.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg648244.html)

When I resolved this two bugs, everything has worked, compiz fusion, video playback even DIRECT RENDERING SUPPORT DRI !!!

have fun!!!

---

### Post by xenobytes on 2008-05-11
I have a fresh install of Ubuntu 8.04 Hardy on a computer and it continues to have this problem while running elisa 0.3.5. 

My elisa.config is default:

```
[general]
version = '0.3.5'
install_date = '2008-05-11'
media_providers = ['daap:daap_media', 'youtube:youtube_media', 'shoutcast:shoutcast_media', 'fspot:fspot_media', 'coherence:upnp_media', 'ipod:ipod_media', 'base:local_media', 'media_db:elisa_media', 'gvfs:gnomevfs_media', 'audiocd:audiocd_media', 'flickr:flickr_media']
metadata_providers = ['media_db:db_metadata', 'gstreamer:gst_metadata_client', 'amazon:amazon_covers']
service_providers = ['updater:updater_service', 'media_db:media_scanner', 'gnome:gnome_screensaver_service', 'hal:hal_service', 'coherence:coherence_service', 'osso:osso_service']
player_engines = ['base:playbin_engine', 'audiocd:cdda_engine']
backends = ['backend1']
frontends = ['frontend1']

[backend1]
activity = 'raval:elisa_activity'
mvc_mappings = 'raval:data/raval_mvc_mappings.conf'
input_providers = ['lirc:lirc_input']

[frontend1]
backend = 'backend1'
theme = 'raval:tango_theme'
input_providers = ['pigment:pigment_input']

[xmlmenu:locations_builder]
locations = []
auto_locations = 1

[media_db:media_scanner]
enabled = '1'
fivemin_location_updates = []
hourly_location_updates = []
daily_location_updates = []
weekly_location_updates = []
unmonitored_locations = []
username = ''
ignored_locations = []
db_backend = 'sqlite'
database = 'elisa.db'
hostname = ''
commit_interval = 5
scan_interval = 0.01
password = ''
generate_thumbnails = False

[media_db:db]
db_backend = 'sqlite'
database = 'elisa.db'

[lirc:lirc_input]
# filename of the LIRC config map to use
lirc_rc = 'streamzap.lirc'
delay = '4'
repeat = '1'

[coherence:coherence_service]
logmode = 'none'
controlpoint = 'yes'

[[plugins]]

[base:service_activity]
# a list of activites, which should beappear in the service_menu
service_activities = ['service:about_activity']

[base:local_media]
hidden_file_chars = '!.'

[player]
audiosink = 'autoaudiosink'

[theme_switcher:theme_switcher_activity]
# a list of themes 'plugin:component' like 'raval:tango_theme'
themes = ['raval:tango_theme', 'raval:poblenou_theme', 'raval:chris_theme']
[updater:updater_service]
# timerange in seconds between 2 refreshes of the plugins cache
update_interval = 86400
[gnome:gnome_screensaver_service]
# Block the Screensaver. Available modes are:   * 1 : block on playing only  *
# 2 : block from the start to the end, use this, if you are only using remotes,
# on which the screensaver is not reacting * else: do not block!
blocking_mode = 2
[youtube:youtube_media]
# Your Youtube username, optional
user = ''
[fspot:fspot_media]
# show hidden photos
show_hidden = 1
# absolute path to f-spot photos.db file
db_path = '/home/gmcquillan/.gnome2/f-spot/photos.db'
[flickr:flickr_media]
# show so many entries should beshown per page?
per_page = '30'
# Your Flickr username (optional)
login = ''
# Your Flickr password (optional)
password = ''
# A list of tags or flickr:// URIs
locations = []
[amazon:amazon_covers]
# set your locale amazon here, could be any of de,jp,ca,uk,fr
locale = ''
[xmlmenu:xmltreemenu_activity]
# Components used to build the menu
menu_builders = ['xmlmenu:activity_node_builder', 'xmlmenu:locations_builder', 'xmlmenu:xdg_entry_builder', 'xmlmenu:playlist_node_builder', 'xmlmenu:menu_node_builder', 'xmlmenu:uri_node_builder']
# Local path to the XML file containing the Elisa menu description
xml_menu = '/home/gmcquillan/.elisa/elisa_menu.xml'
[player:player_controller]
volume_increment_step = '0.02'
seek_backward_step = '15'
seek_forward_step = '30'
show_status_on_ok = '0'
visualisation = 'libvisual_jess'
volume_decrement_step = '0.02'
[pigment:pigment_context]
# If set to 1, the mouse behaviour will be adapted for touchscreen equipped
# hardware.
touchscreen = '0'
# Show/Hide the CPU usage.
show_cpu = '0'
use_gtk = '0'
# Here you can set the width in pixels the window should have at startup. The
# height is computed using screen_ratio. If this value is 0, we decide
# automatically.
window_width = '0'
# Show/Hide the rendering framerate.
show_fps = '0'
# The ratio of the screen. This is a string containing a relation value,
# separated by a colon (:). Common values are 16:9, 4:3, 16:10, but it could be
# any other, too. You can have special values : mm, based on screen size in
# milimeters, sr, based on window manager resolution, or auto. auto will use mm
# special value.
screen_ratio = 'auto'
# If set to 1, Elisa will start fullscreen otherwise windowed
start_fullscreen = '1'
# Show/Hide the memory usage.
show_mem = '0'
[player:playback_view]
# The size the subtitle font should have (in pgm-size)
subtitle_font_size = '0.2'
# the size the visualisation should use for calculating the real size

```

A note that I'm using legacy video hardware pops up the first time I run the program. To be honest, it is old, but an Nvidia Geforce3 should easily be able to handle this rendering; it's running compiz with no problems. 

Is this problem persisting for anyone else who has upgraded to the official hardy release?

Cheers

---

