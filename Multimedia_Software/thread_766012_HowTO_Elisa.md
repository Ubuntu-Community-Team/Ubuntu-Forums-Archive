---
title: "HowTO Elisa"
date: 2008-04-24
forum: Multimedia Software
---

### Post by ajmorris on 2008-04-24
Hello all.

Many people, new and old, to linux, constantly ask about Multimedia in ubuntu, particularly movies.
Elisa is an Open Source application, that plays music, movies, youtube movies, radio etc.

To install it, do the following:
```

gksu gedit /etc/apt/sources.list
```and add this line to that file:
```

deb http://elisa.fluendo.com/packages gutsy main
```then do ```
sudo wget http://elisa.fluendo.com/packages/philn.asc -O - | sudo apt-key add -
``````
sudo apt-get update
sudo apt-get install elisa
```Then, extra packages are also avaliable, elisa-extra and various plugin packages, (to find all elisa things, do sudo apt-cache search elisa)

Elisa, combined with the restricted formats outlined here: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
will be able to play commercial dvds also (like lindvd does) (check the end user license agreements for your area before installing the Restricted Codecs)  (lindvd if you prefer it can be installed in ubuntu via a convert of the Mandriva RPM with alien, although, you have to have bought the Mandriva Powerpack to have permission to use the rpm)

AJ
[B]
EDIT: [/B]Damn, guess this belongs in the Multimedia Productions Sub-Forum, if so, please move it, otherwise, just leave it :)

---

### Post by Joeb454 on 2008-04-25
Thanks, I'll definitely have to look into it (I don't often play movies on my laptop, but for when I do...;))

---

### Post by Maybelline on 2008-04-25
Can some folks please post *useful* elisa.conf configurations?

I keep getting lost in the Elisa ["First Run" wiki]("https://code.fluendo.com/elisa/trac/wiki/FirstRun") page.  Particularly, I'd like to set up several locations like the following, but have never gotten it to work.

[[file:///home/ben/media/videos]]
label = 'Home Videos'
only_media = ['video']
location_type = 'local'

What I end up with is my Rhythmbox DAAP share, the UPnP from Rhythmbox (which doesn't work), and my MythTV stuff shared over UPnP (which sometimes works).  But, I do not get the "local" folders -- I'm expecting a folder called "Home Videos" from the example above.

I *have* previously gotten the autoscan to work, but it continually finds my cover art in my Music folders, and that's not really what I want.

So, basically, I'd just like to see some successful elisa.conf files!

Thanks!!

Here's mine:
```
[general]
    version = '0.3.5'
    install_date = '2008-02-27'
    media_providers = ['daap:daap_media', 'youtube:youtube_media', 'shoutcast:shoutcast_media', 'fspot:fspot_media', 'coherence:upnp_media', 'ipod:ipod_media', 'base:local_media', 'media_db:elisa_media', 'gvfs:gnomevfs_media', 'audiocd:audiocd_media', 'flickr:flickr_media', 'stage6:stage_media']
    metadata_providers = ['media_db:db_metadata', 'gstreamer:gst_metadata_client', 'amazon:amazon_covers']
    service_providers = ['media_db:media_scanner', 'gnome:gnome_screensaver_service', 'hal:hal_service', 'coherence:coherence_service', 'osso:osso_service', 'updater:updater_service']
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
    auto_locations = 0
    
    [[file:///media/SharedStuff/mp3]]
        label = 'SharedStuff MP3s'
        only_media = ['audio']
    [[file:///media/SharedStuff/Movies]]
        label = 'SharedStuff Videos'
        only_media = ['video']
    [[file:///media/SharedStuff/Pics]]
        label = 'SharedStuff Pictures'
        only_media = ['image']


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
    database = 'media.db'
    hostname = ''
    commit_interval = 5
    scan_interval = 0.01
    password = ''
    generate_thumbnails = False

[media_db:db]
    db_backend = 'sqlite'
    database = 'media.db'

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
[gnome:gnome_screensaver_service]
    # Block the Screensaver. Available modes are:   * 1 : block on playing only  *
    # 2 : block from the start to the end, use this, if you are only using remotes,
    # on which the screensaver is not reacting * else: do not block!
    blocking_mode = 1
[youtube:youtube_media]
    # Your Youtube username, optional
    user = ''
[fspot:fspot_media]
    # show hidden photos
    show_hidden = 1
[flickr:flickr_media]
    # show so many entries should beshown per page?
    per_page = '30'
    # Your Flickr username (optional)
    login = ''
    # Your Flickr password (optional)
    password = ''
    # A list of tags or flickr:// URIs
    locations = []
[stage6:stage_media]
    # This is a list of other Stage6-Uris, see CONFIGURATION in the plugins-
    # directory for more informations.
    certain_uris = []
    # The maximum number of other pages to show
    max_pages = 99
    # the password
    password = ''
    # The email which is registered at stage6, optional
    email = ''
    # Show the 'other pages'-item, experimental. See CONFIGURATION for more
    # informations
    pages = 0
[amazon:amazon_covers]
    # set your locale amazon here, could be any of de,jp,ca,uk,fr
    locale = ''
[xmlmenu:xmltreemenu_activity]
    # Components used to build the menu
    menu_builders = ['xmlmenu:activity_node_builder', 'xmlmenu:locations_builder', 'xmlmenu:xdg_entry_builder', 'xmlmenu:playlist_node_builder', 'xmlmenu:menu_node_builder', 'xmlmenu:uri_node_builder']
    xml_menu = '/home/jeremy/.elisa/elisa_menu.xml'
[updater:updater_service]
    # timerange in seconds between 2 refreshes of the plugins cache
    update_interval = 86400
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
    start_fullscreen = '0'
    # Show/Hide the memory usage.
    show_mem = '0'
[playback_view]
    # The size the subtitle font should have (in pgm-size)
    subtitle_font_size = '0.2'
    # the size the visualisation should use for calculating the real size
    visualisation_size = 400
[player:playback_view]
    # The size the subtitle font should have (in pgm-size)
    subtitle_font_size = '0.2'
    # the size the visualisation should use for calculating the real size
    visualisation_size = 400

```

---

### Post by ajmorris on 2008-04-25
Here is my elisa.conf, runs fine for me: (sorry for long post)
```
[general]
version = '0.3.5'
install_date = '2008-04-21'
media_providers = ['daap:daap_media', 'youtube:youtube_media', 'shoutcast:shoutcast_media', 'fspot:fspot_media', 'coherence:upnp_media', 'ipod:ipod_media', 'base:local_media', 'media_db:elisa_media', 'gvfs:gnomevfs_media', 'audiocd:audiocd_media', 'flickr:flickr_media']
metadata_providers = ['media_db:db_metadata', 'gstreamer:gst_metadata_client', 'amazon:amazon_covers']
service_providers = ['media_db:media_scanner', 'gnome:gnome_screensaver_service', 'hal:hal_service', 'coherence:coherence_service', 'osso:osso_service']
player_engines = ['base:playbin_engine', 'audiocd:cdda_engine']
backends = ['backend1']
frontends = ['frontend1']

[backend1]
activity = 'raval:elisa_activity'
mvc_mappings = 'raval:data/raval_mvc_mappings.conf'
input_providers = ['lirc:lirc_input']

[frontend1]
backend = 'backend1'
theme = 'raval:chris_theme'
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
[gnome:gnome_screensaver_service]
# Block the Screensaver. Available modes are:   * 1 : block on playing only  *
# 2 : block from the start to the end, use this, if you are only using remotes,
# on which the screensaver is not reacting * else: do not block!
blocking_mode = 2
[fspot:fspot_media]
# show hidden photos
show_hidden = 1
# absolute path to f-spot photos.db file
db_path = '/home/steve/.gnome2/f-spot/photos.db'
[amazon:amazon_covers]
# set your locale amazon here, could be any of de,jp,ca,uk,fr
locale = ''
[xmlmenu:xmltreemenu_activity]
# Components used to build the menu
menu_builders = ['xmlmenu:activity_node_builder', 'xmlmenu:locations_builder', 'xmlmenu:xdg_entry_builder', 'xmlmenu:playlist_node_builder', 'xmlmenu:menu_node_builder', 'xmlmenu:uri_node_builder']
# Local path to the XML file containing the Elisa menu description
xml_menu = '/home/steve/.elisa/elisa_menu.xml'
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
visualisation_size = 400
[youtube:youtube_media]
# Your Youtube username, optional
user = ''
```Maybelline, where you have:
```
[xmlmenu:locations_builder]
    locations = []
    auto_locations = 0
    
    [[file:///media/SharedStuff/mp3]]
        label = 'SharedStuff MP3s'
        only_media = ['audio']
    [[file:///media/SharedStuff/Movies]]
        label = 'SharedStuff Videos'
        only_media = ['video']
    [[file:///media/SharedStuff/Pics]]
        label = 'SharedStuff Pictures'
        only_media = ['image']
```change it to:

```
[xmlmenu:locations_builder]
    locations = ['file:///media/SharedStuff/mp3', 'file:///media/SharedStuff/Movies' , 'file:///media/SharedStuff/Pics']
    auto_locations = 0
```You only require the different sub sections if you have more than one url with the same name. and you still have to put them in the locations = '' section still if you have multiple sub-sections.

Hope it works :)

AJ

---

### Post by Maybelline on 2008-04-26
> **ajmorris said:**
> 
Maybelline, where you have:
```
[xmlmenu:locations_builder]
    locations = []
    auto_locations = 0
    
    [[file:///media/SharedStuff/mp3]]
        label = 'SharedStuff MP3s'
        only_media = ['audio']
    [[file:///media/SharedStuff/Movies]]
        label = 'SharedStuff Videos'
        only_media = ['video']
    [[file:///media/SharedStuff/Pics]]
        label = 'SharedStuff Pictures'
        only_media = ['image']
```change it to:

```
[xmlmenu:locations_builder]
    locations = ['file:///media/SharedStuff/mp3', 'file:///media/SharedStuff/Movies' , 'file:///media/SharedStuff/Pics']
    auto_locations = 0
```You only require the different sub sections if you have more than one url with the same name. and you still have to put them in the locations = '' section still if you have multiple sub-sections.


Perfection!  Thank you so much!  Also, in case it helps anyone else, I was getting no visualizations at first.  Add the package libvisual-0.4-plugins (or similar), and restart Elisa.  After that, you're golden.  Thanks AJ!

---

### Post by zeezam on 2008-07-13
Any that runs Elisa on Ubuntu 8.04? My Elisa hangs when I try to open configurations in Elisa it hangs.

I haven't find any documentations or "how to" install plugins. I want flickr, youtube functions etc...

---

### Post by fazza on 2008-07-13
yeah me too :(
I ran it on 7.10 and it had potential to be really nice...
btw I've got a 64bit pc if it makes any difference

---

### Post by zeezam on 2008-07-14
How is it with the Elisa plugins? Is it installed as standard?

How do I use the plugins, couldn't find them in the menu.

---

### Post by fosix on 2008-07-14
I tried this on my Drapper Ubuntu by replacing Gutsy with Drapper, but it did not work. Why?> deb [http://elisa.fluendo.com/packages](http://elisa.fluendo.com/packages) gutsy main

---

### Post by ajmorris on 2008-07-19
> **zeezam said:**
> Any that runs Elisa on Ubuntu 8.04? My Elisa hangs when I try to open configurations in Elisa it hangs.

I haven't find any documentations or "how to" install plugins. I want flickr, youtube functions etc...

Not sure about for gutsy... if you use the .deb file, it could be an old version, unless someone that is not from elisa has specifically packaged a deb file, as elisa states that they have no .deb or .rpm packages for 0.5.1, you may be better off compiling it.

As for plugins:
[http://elisa.fluendo.com/plugins/](http://elisa.fluendo.com/plugins/)
and this may help:
[http://elisa.fluendo.com/documentation](http://elisa.fluendo.com/documentation)

AJ

---

### Post by ajmorris on 2008-07-19
> **fosix said:**
> I tried this on my Drapper Ubuntu by replacing Gutsy with Drapper, but it did not work. Why?

it is dapper not drapper, however, it will not exist for dapper, elisa was developed well after dapper, and a repository for it will not exist

AJ

---

### Post by Anthony M on 2008-07-20
> **ajmorris said:**
> Not sure about for gutsy... if you use the .deb file, it could be an old version, unless someone that is not from elisa has specifically packaged a deb file, as elisa states that they have no .deb or .rpm packages for 0.5.1, you may be better off compiling it.

As for plugins:
[http://elisa.fluendo.com/plugins/](http://elisa.fluendo.com/plugins/)
and this may help:
[http://elisa.fluendo.com/documentation](http://elisa.fluendo.com/documentation)

AJ

Is anyone else getting a page load error for the elisa site?

---

