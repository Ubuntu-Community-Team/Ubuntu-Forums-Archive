---
title: "Wanted: working Freevo local_config.py file"
date: 2007-01-05
forum: Multimedia &amp; Video
---

### Post by megamaced on 2007-01-05
I've installed Freevo via a 3rd party repository and now I need to configure it via the ~/.freevo/local_config.py file.

I run Dapper Drake and watch TV through a Hauppauge Nova-T 909 with UK TV listings.

I'd be very greatful if someone could share their config file. Thanks :)

---

### Post by G|N| on 2007-01-06
I live in Belgium and my tv card uses ivtv so some things will be different in your config!
```

CONFIG_VERSION = 5.16
FREEVO_CACHEDIR = '/var/cache/freevo'
# ======================================================================
# General freevo settings:
# ======================================================================                                        # 'VOL', 'PCM' 'OGAIN' etc.
#CONTROL_ALL_AUDIO   = 1               # Should Freevo take complete control of audio
MAX_VOLUME          = 70              # Set what you want maximum volume level to be.
DEFAULT_VOLUME      = 70              # Set default volume level.
TV_IN_VOLUME        = 70              # Set this to your preferred level 0-100.
START_FULLSCREEN_X  = 0               # Start in fullscreen mode if using x11 or xv.
CONFIRM_SHUTDOWN    = 1               # ask before shutdown
#ROM_DRIVES = [ ('/media/cdrom0', '/dev/hdc', 'dvd') ]
HIDE_UNUSABLE_DISCS = 1               
ENABLE_SHUTDOWN_SYS = 0
#SHUTDOWN_SYS_CMD = "sudo shutdown -h now"
# ======================================================================
# Events
# ======================================================================
USE_NETWORK = 1
CACHE_IMAGES = 1
EVENTS['menu']['REC']  = Event(MENU_CALL_ITEM_ACTION, arg='queue_a_track')
EVENTS['menu']['SAVE'] = Event(MENU_CALL_ITEM_ACTION, arg='close_playlist')
# ======================================================================
# Plugins:
# ======================================================================
plugin.activate('audio.album_tree')
AUDIO_ALBUM_TREE_SPEC = []
AUDIO_ALBUM_TREE_SPEC.append({'name':'(A-Z)/Artist/Album-Year/Track'
    ,'spec':["upper(substr(artist,0,1))"
            ,"artist","album||'-'||year"
            ,"track||'-'||title"]
    ,'alt_grouping':[None,None,'year||album','track']
    })

plugin.remove('idlebar.clock')
plugin.activate('idlebar.clock', args=('%a %H:%M'))

plugin.activate('idlebar.volume')

plugin.activate('audio.coversearch', args=('key',) )

plugin.activate('shoppingcart')

plugin.activate('df')

plugin.remove('headlines')
plugin.activate('headlines', level=45)
HEADLINES_LOCATIONS = [
        ('OpenSourceNiews.nl', 'http://www.opensourcenieuws.nl/index2.php?option=com_rss&feed=RSS2.0&no_html=1'),
        ('Freevo news', 'http://sourceforge.net/export/rss2_projnews.php?group_id=46652&rss_fulltext=1'), 
        ('Freevo releases', 'http://sourceforge.net/export/rss2_projfiles.php?group_id=46652'), 
        ('vrt nieuws', 'http://rss.vrtnieuws.net/nieuwsnet_master/versie2/systeem/rss/nnII_nieuws_hoofdpunten/index.xml') ]

plugin.activate( 'weather', level=45)
PLUGIN_WEATHER_LOCATIONS=[("BEXX0003",1, "Antwerp (Belgium)")]

plugin.activate('usb')
USB_HOTPLUG = [ ('066f:8252', 'Mounting USB stick', 'mount /dev/sda1 /media/usb') ]
plugin.activate('usbstorage', type='image', args=('USB Stick', '/media/usb'))
plugin.activate('usbstorage', type='video', args=('USB Stick', '/media/usb'))
plugin.activate('usbstorage', type='audio', args=('USB Stick', '/media/usb'))

plugin.remove('tv.generic_record')
plugin_record = plugin.activate('tv.ivtv_record')
plugin.activate('tv.ivtv_xine_tv')

plugin.activate('video.details')
plugin.activate('audio.playlist')

# ======================================================================
# Freevo directory settings:
# ======================================================================
DIRECTORY_SMART_SORT = 1
DIRECTORY_AUTOPLAY_SINGLE_ITEM = 0
DIRECTORY_FORCE_SKIN_LAYOUT = -1
DIRECTORY_USE_MEDIAID_TAG_NAMES = 1
DIRECTORY_CREATE_PLAYLIST      = [ 'audio', 'image', 'video']
DIRECTORY_ADD_PLAYLIST_FILES   = [ 'audio', 'video' ]

# ======================================================================
# Freevo movie settings:
# ======================================================================
VIDEO_ITEMS = [ ('movies', '/media/muziek/movies') ]
VIDEO_MPLAYER_SUFFIX = [ 'avi', 'mpg', 'mpeg', 'wmv', 'bin', 'rm',
                          'divx', 'ogm', 'asf', 'm2v', 'm2p',
                          'mp4', 'viv', 'nuv', 'mov',
                          'nsv', 'mkv' ]
VIDEO_XINE_SUFFIX = [ 'isp', 'vob', 'ts' ]
VIDEO_PREFERED_PLAYER = 'mplayer'

# ======================================================================
# Freevo audio settings:
# ======================================================================
AUDIO_ITEMS = [ ('sixties', '/media/muziek/full-albums/sixties/'),
                ('blues', '/media/muziek/full-albums/blues') ]
AUDIO_COVER_REGEXP = 'front|cover'

# ======================================================================
# Freevo image viewer settings:
# ======================================================================
IMAGE_ITEMS = [ ('pics', '/media/Images') ]
IMAGE_SUFFIX = [ 'jpg','gif','png', 'jpeg','bmp','tiff','psd' ]
IMAGE_SSHOW_SUFFIX = [ 'ssr' ]
IMAGEVIEWER_BLEND_MODE = 0  


# ======================================================================
# Freevo games settings:
# ======================================================================

# ======================================================================
# Freevo SKIN settings:
# ======================================================================


# ======================================================================
# Freevo OSD settings:
# ======================================================================

OSD_OVERSCAN_X = 35
OSD_OVERSCAN_Y = 25
    
# ======================================================================
# Freevo remote control settings:
# ======================================================================

# ======================================================================
# TVtime settings:
# ======================================================================

# ======================================================================
# MPlayer settings:
# ======================================================================

# ======================================================================
# Xine settings:
# ======================================================================
XINE_ARGS_DEF = ' --post tvtime:method=LineDoubler,enabled=1,pulldown=none,framerate_mode=half_top,judder_correction=0,use_progressive_frame_flag=1,chroma_filter=0,cheap_mode=1'


# ======================================================================
# IVTV Xine TV settings:
# ======================================================================

XINE_TV_TIMESHIFT_FILEMASK = "/home/wout/xine-buf-"

# ======================================================================
# Freevo TV settings:
# ======================================================================
TV_RECORD_DIR = '/media/movies'
VIDEO_SHOW_DATA_DIR = '/media/muziek/movies'
TV_SETTINGS= 'pal television europe-west /dev/video0'
TV_DRIVER = 'v4l2'
TV_DEVICE = '/dev/video0'
TV_INPUT = 'television'
#second tv card
#TV_DRIVER_2 = 'v4l2'
#TV_DEVICE_2 = '/dev/video1'
#TV_INPUT_2  = '0'
#AUDIO_DEVICE_2 = '/dev/dsp1'
TV_SETTINGS = '%s television %s %s' % (CONF.tv, CONF.chanlist, TV_DEVICE)
#TIMESHIFT_BUFFER_SIZE = 128
#TIMESHIFT_ENCODE_CMD = 'mp1e -m3 -c%s -p%s -r14,100' % \
#                        (TV_SETTINGS.split()[3], AUDIO_INPUT_DEVICE) 
#TIMESHIFT_BUFFER = '%s/timeshift.mpeg' % FREEVO_CACHEDIR
TV_DATEFORMAT = '%e-%b' # Day-Month: 11-Jun
TV_TIMEFORMAT = '%H:%M' # Hour-Minute 14:05
TV_DATETIMEFORMAT = '%A %b %d %I:%M %p' # Thursday September 24 8:54 am
TV_RECORDFILE_MASK = '%%m-%%d %%H:%%M %(progname)s - %(title)s'
TV_RECORD_SCHEDULE = '%s/record_schedule.xml' % FREEVO_CACHEDIR
TV_RECORD_SERVER_IP = 'localhost'
TV_RECORD_SERVER_PORT = 18001
TV_RECORD_PADDING = 5 * 60

TV_IVTV_OPTIONS = {
    'input'         : 0,
    'resolution'    : '640x480',
    'aspect'        : 2,
    'audio_bitmask' : 233,
    'bframes'       : 3,
    'bitrate_mode'  : 1,
    'bitrate'       : 4000000,
    'bitrate_peak'  : 4000000,
    'dnr_mode'      : 0,
    'dnr_spatial'   : 0,
    'dnr_temporal'  : 0,
    'dnr_type'      : 0,
    'framerate'     : 0,
    'framespergop'  : 15,
    'gop_closure'   : 1,
    'pulldown'      : 0,
    'stream_type'   : 10,
}

FREQUENCY_TABLE = {
	'een': 203250,
	'canvas': 252250,
	'vtm': 224250,
	'ka2': 280250,
	'vt4' : 266250,
	'tmf': 238250,
	'mtv': 245250,
	'jim': 259250,
	'vijftv': 175250,
	'ngc': 442250,
	'rtv': 196250,
	'ned1': 189250,
	'ned2' : 273250,
	'ned3': 210250,
	'bbc1': 399250,
	'bbc2' : 140250,
	'la1': 217250,
	'la2': 182250,
	'rtl': 147250
}

TV_CHANNELS = [
('een', 'een', 		'een'),
('canvas', 'canvas', 	'canvas', ('1234567', '0700', '1959')),
('vtm', 'VTM', 		'vtm'),
('ka2', 'Kanaal 2', 'ka2'),
('vt4', 'VT4', 		'vt4'),
('tmf', 'TMF', 		'tmf'),
('mtv', 'MTV', 	'mtv', ('1234567', '1800', '0559')),
('jim', 'Jim', 		'jim'),
('vijftv', 'vijftv', 	'vijftv', ('1234567', '1300', '1159')),
('ngc', 'Nat geo', 	'ngc'),
('rtv', 'rtv', 		'rtv'),
('ned1', 'nederland 1', 'ned1'),
('ned2', 'nederland 2', 'ned2'),
('ned3', 'nederland 3', 'ned3'),
('bbc1', 'bbc 1', 	'bbc1'),
('bbc2', 'bbc 2', 	'bbc2'),
('la1', 'La Une' , 	'la1'),
('la2', 'La Deux', 	'la2'),
('rtl', 'RTL-TVi', 	'rtl') ]


# ======================================================================
# Freevo builtin WWW server settings:
# ======================================================================
plugin.activate('www')
WEBSERVER_PORT = 9999
WWW_USERS = { "user" : "password", "admin": "password" } 

# ======================================================================
# Internal stuff, you shouldn't change anything here unless you know
# what you are doing
# ======================================================================
XMLTV_FILE = '/home/me/TV.xml'
LOCALE='latin-1'
#LOCALE='utf-8'
ENABLE_NETWORK_REMOTE = 1
REMOTE_CONTROL_HOST = '127.0.0.1'
REMOTE_CONTROL_PORT = 16310

```

---

### Post by megamaced on 2007-01-07
Thanks for that! It looks pretty complicated but I'll soldier on!

---

