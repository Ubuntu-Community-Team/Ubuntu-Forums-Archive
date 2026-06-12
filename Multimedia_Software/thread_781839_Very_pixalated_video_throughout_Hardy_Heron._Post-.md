---
title: "Very pixalated video throughout Hardy Heron. Post-processing?"
date: 2008-05-04
forum: Multimedia Software
---

### Post by not-a-bot on 2008-05-04
While trying to find the reason for this I stumbled upon quite a few very similar descriptions of the problem. All of them describe the same problem on different builds and variations of Ubuntu and not a single one even received one reply. So hopefully I will be more lucky than the previous thread starters.

Playing back video in Ubuntu 8.04 (Hardy Heron) simply looks bad. It's not horribly bad but it simply looks much worse than the playing the same file on Windows or OS X.
The files are notably pixelated and and look bad even when comparing to playback on Windows without post-processing. This is especially noticeable in fullscreen or at least sufficiently zoomed playback.

It doesn't seem to matter if Compiz is enabled or disabled. And it doesn't seem to matter if playing the files in Totem or in VLC.

I installed ubuntu-restricted-extras and gstreamer-ffmpeg seems to do the decoding for xvid files in Totem now. However I have no idea how to even enable the incredibly important post-processing in Totem / gstreamer at all.

I can up the post-processing in VLC up to 6. But this setting does not alter the video quality at all. The video looks just as bad as in Totem. And for some reason the setting doesn't even stick and always falls back to 0 when opening a new file in VLC (I guess I simply didn't find the setting to make it stick).

So I don't even know if post-processing is the problem since I don't even know how to successfully activate it. :(

My grafics card is a Ati Radeon x1900 XT and I'm using the official restricted drivers (catalyst 8.3) that Hardy Heron currently offers ... since EnvyNG doesn't support a newer version yet I'm unwilling to give the 8.4 version a shot yet.

I hopw that someone can at least confirm this problem and / or maybe tell me how to activate ffmpeg's great post-processing in Totem so I can figure out if that is the root fo the problem or not.

---

### Post by st0nedpenguin on 2008-05-04
Check to see what output plugin you're using in VLC, the X11 one gives me horribly pixellated video, the Xv one is a lot better.

You'll probably have to disable Compiz though or you'll get windowed video flicker with the Xv output, gotta love those ATi drivers.

---

### Post by spandanj on 2008-05-10
i have the same problem: fullscreen video is very pixellated!

I am on dell 6400 with ati radeon x1400


- IS THERE ANY SOLUTION?

---

### Post by omi on 2008-05-11
Hi people,

I've also problems with Ubuntu 8.04/ATI/PIXELATED VIDEOS

I'd installed Ubuntu 8.04 but still have problems with video playback of *.avi files with Totem.

I'd installed:
- ATI driver from System -> Administration -> Hardware Drivers

* Advanced Video Effects are disabled

Also I'd done this (according to ubuntuguide.org->media codecs):

```
sudo apt-get install gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-ffmpeg libxine1-ffmpeg libdvdread3
```

Also I'd done this (after adding mediabuntu repository):

```
sudo ubuntu-restricted-extras
sudo apt-get install w32codecs
sudo apt-get install lame
sudo apt-get install sox
sudo apt-get install ffmpeg
sudo apt-get install mjpegtools
sudo apt-get install vorbis-tools
```

I've downloaded and played [http://ed.plonkmedia.org/Elephants_Dream_HD.avi](http://ed.plonkmedia.org/Elephants_Dream_HD.avi) 

..and here everything is okay, there is no pixelization and the playback is great.

**But still has choppy video while playing *.AVI (DIVX/XVID - DVD Rips) files with Totem and VLC. There is some pixelization of the movies.**

I was searching for a solution in the forum but didn't find it so I'm starting this thread. Have no problems with anything else in Ubuntu 8.04. I'm using HP Compaq 6820s Laptop with ATI video card.

Hope someone can help.

---

### Post by matteo.gazzoni on 2008-05-11
Hi, try to take a look at [this]("http://forum.compiz-fusion.org/showthread.php?t=6794").

Modify xorg.conf as they say, then restart.

Lastly make sure you have compiz disabled, at least, if you don't want flickering issues with windowed video playback!

[Test it with VLC, Default Video Plugin (Xv)]

---

### Post by pterosky on 2008-05-12
I was getting the same pixeled image in VLC and trying to open an AVI file with Mplayer I got ```
Error opening/initializing the selected video_out (-vo) device.
```

Somebody posted a solution [here]("http://ubuntuforums.org/showthread.php?t=137560"), answer nr 5: 

> 1) are you using the fglrx driver?

2) if so, add this to the "Device" section of /etc/X11/xorg.conf ```

     Option "VideoOverlay" "on"
     Option "OpenGLOverlay" "off"
```

Save the file, restart X and try the xv output again.


It did the trick for VLC! No more pixelation AND Mplayer is now able to play in glorious full screen mode. Before the full screen mode did go full screen, but left the picture small in the center.

I am not sure what VideoOverlay or OpenGLOverlay means, just glad this little annoyance is gone. I was ready to ditch Hardy and go for Gutsy :)

EDIT: New problem, VideoOverlay set to "on" removes picture in VLC in the TV, instead displaying a blue colour. The desktop is getting through no problem...

---

### Post by omi on 2008-05-13
I've tryed the last post but this doesn't help me :(

---

### Post by cor2y on 2008-05-13
Does the video in question play clean and clear on a windows pc?
If yes then you may need to change your decoders.
For example by default totem uses the gstreamer plugins for video and this time around its a bit lacking avi files have artifacts in them during playback so the solution for this is to install totem-xine with the xine library.
In this version of hardy you have the option of keeping both totem-gstreamer and totem-xine installed together so you will have to select totem-xine as the default media player or uninstall totem-gstreamer
To uninstall totem-gstreamer and install totem-xine
```
sudo apt-get install totem-xine
sudo apt-get remove totem-gstreamer
```
To just install totem-xine and make it the default media player```
sudo apt-get install totem-xine
sudo update-alternatives --config totem
```
Then select totem-xine as the default media player.
Now try video playback if it is still all pixels , then disable compiz-fusion if in use or use the video playback plugin for compiz-fusion.
If that fails then try installing the ubuntu closed drivers for your video chipset if not installed.

---

### Post by matteo.gazzoni on 2008-05-13
Ok, I'll try to make it *simple*, whoever has an **X1050 or newer card** (with the **latest ATI proprietary drivers**) can replace his [Device] section in the [xorg.conf] with that (backup it first):

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
	Option		"XAANoOffscreenPixmaps"		"on"
	Option		"VideoOverlay"			"off"
	Option		"OpenGLOverlay"			"off"
	Option		"TexturedVideo"			"on"
	Option		"TexturedVideoSync"		"on"
	Option		"Textured2D"			"on"
	Option		"TexturedXrender"		"on"
	Option		"BackingStore"			"on"
	Option		"UseFastTLS"			"1"
EndSection
```


**And restart X (or Ubuntu itself)**


**Note 1**: If you want to use compiz and at the same time have a decent full screen video playback (I've said full screen, because the windowed mode still flickers) then open [VLC] and go to:
[Preferences] > [Video] > [Output modules] select [XVideo] (the default one should be right in most cases though), expand [Output modules] menu and under [XVideo] set the flag to [Alternate fullscreen method]

**Note 2**: If compiz isn't that cool for you, disable it and you'll have either windowed mode and full screen mode as they should be.

---

### Post by omi on 2008-05-14
You are a golden boy matteo.gazzoni! **Finally it works!**.
Don`t forget to replace totem-gstreamer with totem-xine.

10x a lot for community support!

Here I've gathered all useful information from this topic problem:
[http://stavrev.net/linux/ati-radeon-hardy-heron](http://stavrev.net/linux/ati-radeon-hardy-heron)

---

### Post by sloggerkhan on 2008-05-14
for the guy who was worried about getting the latest ati fglrx drivers, you can now creat *.deb files for Ubuntu with the ati installer and have the new drivers installed and managed in synaptic/aptitude/etc. It's actually pretty easy.

PS: The fglrx xv overlay is pretty good (somewhat better than nvidia's IMO), but if you want to turn off compiz and set the overlay to open GL, you can video scaling that's so good standard def almost looks hi-def when upscaled at the cost of tremendous cpu/gpu load.

---

### Post by Wyld on 2008-05-15
I'm finding the same issues; cpu usage is high, choppy vlc, etc ..

But I'm using the closed *nvidia* drivers with my 9800glx.

Hmm.

---

### Post by JacquiOh on 2008-05-15
I've been having this problem since I started using Ubuntu and today I installed mplayer. When I tried the videos in mplayer, the videos were perfect. BUT when I tried them again in gstreamer, they were perfect too.

I don't know what happened but it might work for other people too.

---

### Post by primlinOS on 2008-05-18
I am having the same issues.  VLC, mplayer, in fact any fullscreen video is very pixelated and choppy.  I have a radeonR350 9800 pro and am running the ATI accelerated graphics restricted driver.  The video was running fine under 7.10 (after some work), but after upgrading to 8.04 it's broken.  I have compiz running as well.  

Do I just need to edit the driver info in xorg.conf, as matteo suggested?  If so, would anybody be willing to explain what exactly is causing the issues?  All thanks.

---

### Post by primlinOS on 2008-05-18
So I've tried Matteo's suggestion by editing the xorg.conf file, restarting.  mplayer and VLC still both don't work correctly, in fact totem has the same problems as do web-browser based videos.  Seems there is something basic that is wrong here?

---

### Post by matteo.gazzoni on 2008-05-18
I suggest you to watch this [page]("http://forum.compiz-fusion.org/showthread.php?t=6794") and play around.

---

### Post by primlinOS on 2008-05-19
Thanks matteo, I'll look into this.  But maybe I should note that turning compiz off does not improve the video playback; in fact, oddly, it seems to make it worse.

---

### Post by matteo.gazzoni on 2008-05-19
Actually the owners of an **ATI X1050 or newer card** (with the latest **ATI proprietary drivers**) that disable:

```
Option "VideoOverlay" "off"
Option "OpenGLOverlay" "off"
```

and that use instead:

```
Option "TexturedVideo" "on"
```

will get serious benefits in disabling Compiz (one word: video flickering).

About the older cards, _VideoOverlay_ should be set to active and the other two disabled.

*If none of this helps, I would try to disable compiz; then try both ATI proprietary drivers and Ubuntu default drivers, while using the configuration given in "About the older cards". Trying to disable AIGLX (from xorg.conf) could be another alternative.*

---

### Post by primlinOS on 2008-05-20
Thanks for the suggestions matteo, the video is now running pretty smooth in window mode, but fullscreen mode is still completely broken in all apps.  I have:

```
Section "Device"
	Identifier	"ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]"
	Driver		"fglrx"
	Busid		""
  	Option 		"XAANoOffscreenPixmaps" "on"	
	Option          "VideoOverlay" "on"
	Option          "OpenGLOverlay" "off"
	Option          "TexturedVideo" "off"
	Option 		"Textured2D" "off"
	Option 		"TexturedXrender" "off"
EndSection
```

and I have tried with and without

```
Section "ServerLayout"
	Option          "AIGLX" "on"
  screen "Default Screen"
EndSection

```

Not sure what to try next.  I'll keep poking around, but any more suggestions would also be appreciated.

---

### Post by pterosky on 2008-05-21
The image stayed the same size and the border around the image went black if I selected Fullscreen(f) in Mplayer. I solved the problem by opening Preferences > video and changing it to to gl - X11(OpenGL) -- no editing in xorg.conf.

Selecting GL for Video Output also fixed a problem I had with my Real Player plug-in in Firefox -- there was sound but no picture, only the path to the stream. Solution: Right-click in the Real Player plug-in window, click Preferences and set Video output to GL.

---

### Post by primlinOS on 2008-05-22
Okay, here the error messages when I run mplayer, can anybody please help? -- :)

Sorry for the long post, and please note, mplayer and all video ran perfectly before I upgraded to heron:

-------------------

main: app name: smplayer
global_init
global_init: config file: '/home/michoski/.smplayer/smplayer.ini'
Preferences::load
Debug: Translator::loadCatalog: can't load qt_en_US from /usr/share/smplayer/translations
Debug: Translator::loadCatalog: can't load qt_en_US from /usr/share/qt4/translations
Debug: Translator::loadCatalog: successfully loaded smplayer_en_US from /usr/share/smplayer/translations
This is SMPlayer v. 0.6.0rc2 (SVN 834) running on Linux
Debug: This is SMPlayer v. 0.6.0rc2 (SVN 834) running on Linux
Debug: Qt v. 4.3.3
Debug: main: files_to_play: count: 0
Debug: main: changed working directory to app path
Debug: main: current directory: /usr/bin
Debug: Recents::load /smplayer_files.ini'
Debug: MplayerProcess::init_rx
Debug: MplayerLayer::allowClearingBackground: 0
Debug: Preferences::monitor_aspect_double
Debug:  warning: monitor_aspect couldn't be parsed!
Debug:  monitor_aspect set to 0
Debug: Playlist::setModified: 0
Debug: Playlist::loadSettings
Debug: Playlist::addItem: '/media/sda3/Film/Factory Girl/factory_girl-2006-dvdrip-en.avi'
Debug: Playlist::setModified: 0
Debug: name: 'factory_girl-2006-dvdrip-en.avi'
Debug: Style name: 'plastique'
Debug: Style class name: 'QPlastiqueStyle'
Debug: BaseGui::initializeMenus
Debug: BaseGui::initializeMenus
Debug: BaseGui::updateRecents
Debug: BaseGui::updateWidgets
Debug: BaseGui::updateWidgets
Debug: BaseGui::updateRecents
Debug: PlaylistDock::hideEvent: isFloating: 0
Debug:  undocked
Debug: PlaylistDock::showEvent: isFloating: 1
Debug: PlaylistDock::hideEvent: isFloating: 1
Debug: BaseGui::initializeMenus
Debug: BaseGui::updateRecents
Debug: BaseGui::updateWidgets
Debug: BaseGuiPlus::loadConfig
Debug: DefaultGui::createStatusBar
Debug: DefaultGui::createActions
Debug: DefaultGui::createControlWidget
Debug: TimeSlider::setDragDelay: 100
Debug: DefaultGui::createControlWidgetMini
Debug: TimeSlider::setDragDelay: 100
Debug: TimeSlider::setDragDelay: 100
Debug: BaseGui::initializeMenus
Debug: BaseGui::updateRecents
Debug: DefaultGui::updateWidgets
Debug: BaseGui::updateWidgets
Debug: DefaultGui::loadConfig
Debug: DefaultGui::updateWidgets
Debug: BaseGui::updateWidgets
Debug: BaseGui::showEvent
Debug: BaseGui::loadActions
Debug: ActionsEditor::loadFromConfig
Debug: BaseGui::initializeMenus
Debug: BaseGui::updateRecents
Debug: DefaultGui::updateWidgets
Debug: BaseGui::updateWidgets
Debug: BaseGui::fileOpen
Debug: BaseGui::openFile: '/media/sda3/Film/Factory Girl/factory_girl-2006-dvdrip-en.avi'
Debug: Core::openFile: '/media/sda3/Film/Factory Girl/factory_girl-2006-dvdrip-en.avi'
Debug: Core::playNewFile: '/media/sda3/Film/Factory Girl/factory_girl-2006-dvdrip-en.avi'
Debug: Core::saveMediaInfo
Debug: Core::checkHaveSettingsSaved: group_name: '_media_sda3_Film_Factory_Girl_factory_girl-2006-dvdrip-en_avi_648178688'
Debug: We have settings for this file!!!
Debug: Core::loadMediaInfo: '_media_sda3_Film_Factory_Girl_factory_girl-2006-dvdrip-en_avi_648178688'
Debug: MediaSettings::load
Debug: Media settings read
Debug: Core::playNewFile: volume: 100, old_volume: 40
Debug: Core::initPlaying
Debug: Core::startMplayer
Debug: Core::startMplayer: setting working directory to '/home/michoski/.smplayer/screenshots'
Debug: DesktopInfo::desktop_size: primary screen: 0
Debug: DesktopInfo::desktop_size: size of primary screen: 1600 x 1200
Debug: DesktopInfo::desktop_size: size of screen: 1600 x 1200
Debug: MplayerVersion::isMplayerAtLeast: comparing 24924 with 24722
Debug: Core::startMplayer: command: '/usr/bin/mplayer -noquiet -nofs -sub-fuzziness 1 -identify -slave -vo x11 -ao pulse -zoom -nokeepaspect -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 52428814 -colorkey 0x020202 -monitoraspect 1.33333 -subfont-autoscale 1 -subfont-text-scale 5 -subcp ISO-8859-1 -aid 1 -subpos 100 -contrast 0 -brightness 0 -hue 0 -saturation 0 -nocache -ss 48 -osdlevel 0 -vf-add screenshot -channels 2 /media/sda3/Film/Factory Girl/factory_girl-2006-dvdrip-en.avi'
Debug: MplayerLayer::playingStarted
Debug: BaseGui::calculateDiff: diff_size: 0, 0
Debug: BaseGui::calculateDiff: diff_size set to: 0, 131
Debug: MplayerProcess::init_rx
Debug: Playlist::setModified: 0
Debug: Playlist::addFiles
Debug: Playlist::addItem: '/media/sda3/Film/Factory Girl/factory_girl-2006-dvdrip-en.avi'
Debug: name: 'factory_girl-2006-dvdrip-en.avi'
Debug:  * latest_dir: ''
Debug: MplayerProcess::parseLine: 'MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team'
Debug: MplayerVersion::mplayerVersion: MPlayer version found: 1.0rc2
Debug: MplayerProcess::parseLine: MPlayer SVN: 24722
Debug: MplayerProcess::parseLine: 'CPU: Intel(R) Pentium(R) 4 CPU 2.40GHz (Family: 15, Model: 3, Stepping: 3)'
Debug: MplayerProcess::parseLine: 'CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1'
Debug: MplayerProcess::parseLine: 'Compiled with runtime CPU detection.'
Debug: MplayerProcess::parseLine: 'mplayer: could not connect to socket'
Debug: MplayerProcess::parseLine: 'mplayer: No such file or directory'
Debug: MplayerProcess::parseLine: 'Failed to open LIRC support. You will not be able to use your remote control.'
Debug: MplayerProcess::parseLine: ''
Debug: MplayerProcess::parseLine: 'Playing /media/sda3/Film/Factory Girl/factory_girl-2006-dvdrip-en.avi.'
Debug: MplayerProcess::parseLine: 'AVI file format detected.'
Debug: MplayerProcess::parseLine: 'ID_VIDEO_ID=0'
Debug: MplayerProcess::parseLine: '[aviheader] Video stream found, -vid 0'
Debug: MplayerProcess::parseLine: 'ID_AUDIO_ID=1'
Debug: MplayerProcess::parseLine: ID_AUDIO_ID: 1
Debug: MplayerProcess::parseLine: '[aviheader] Audio stream found, -aid 1'
Debug: MplayerProcess::parseLine: 'VIDEO:  [DX50]  640x360  24bpp  25.000 fps  765.2 kbps (93.4 kbyte/s)'
Debug: MplayerProcess::parseLine: 'ID_FILENAME=/media/sda3/Film/Factory Girl/factory_girl-2006-dvdrip-en.avi'
Debug: MplayerProcess::parseLine: 'ID_DEMUXER=avi'
Debug: MplayerProcess::parseLine: 'ID_VIDEO_FORMAT=DX50'
Debug: MplayerProcess::parseLine: 'ID_VIDEO_BITRATE=765216'
Debug: MplayerProcess::parseLine: 'ID_VIDEO_WIDTH=640'
Debug: MplayerProcess::parseLine: md.video_width set to 640
Debug: MplayerProcess::parseLine: 'ID_VIDEO_HEIGHT=360'
Debug: MplayerProcess::parseLine: md.video_height set to 360
Debug: MplayerProcess::parseLine: 'ID_VIDEO_FPS=25.000'
Debug: MplayerProcess::parseLine: 'ID_VIDEO_ASPECT=0.0000'
Debug: MplayerProcess::parseLine: md.video_aspect set to 1.777778
Debug: MplayerProcess::parseLine: 'ID_AUDIO_FORMAT=85'
Debug: MplayerProcess::parseLine: 'ID_AUDIO_BITRATE=128000'
Debug: MplayerProcess::parseLine: 'ID_AUDIO_RATE=0'
Debug: MplayerProcess::parseLine: 'ID_AUDIO_NCH=0'
Debug: MplayerProcess::parseLine: 'ID_LENGTH=5742.56'
Debug: MplayerProcess::parseLine: md.duration set to 5742.560000
Debug: MplayerProcess::parseLine: 'Xlib:  extension "XFree86-VidModeExtension" missing on display ":1.0".'
Debug: MplayerProcess::parseLine: 'xscreensaver_disable: Could not find XScreenSaver window.'
Debug: MplayerProcess::parseLine: 'GNOME screensaver disabled'
Debug: MplayerProcess::parseLine: 'Opening video filter: [screenshot]'
Debug: MplayerProcess::parseLine: '=========================================================================='
Debug: MplayerProcess::parseLine: 'Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family'
Debug: MplayerProcess::parseLine: 'Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)'
Debug: MplayerProcess::parseLine: '=========================================================================='
Debug: MplayerProcess::parseLine: 'ID_VIDEO_CODEC=ffodivx'
Debug: MplayerProcess::parseLine: '=========================================================================='
Debug: MplayerProcess::parseLine: 'Forced audio codec: mad'
Debug: MplayerProcess::parseLine: 'Opening audio decoder: [libmad] libmad mpeg audio decoder'
Debug: MplayerProcess::parseLine: 'AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)'
Debug: MplayerProcess::parseLine: 'ID_AUDIO_BITRATE=128000'
Debug: MplayerProcess::parseLine: 'ID_AUDIO_RATE=44100'
Debug: MplayerProcess::parseLine: 'ID_AUDIO_NCH=2'
Debug: MplayerProcess::parseLine: 'Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)'
Debug: MplayerProcess::parseLine: '=========================================================================='
Debug: MplayerProcess::parseLine: 'AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)'
Debug: Core::gotAO: 'pulse'
Debug: MplayerProcess::parseLine: 'ID_AUDIO_CODEC=mad'
Debug: MplayerProcess::parseLine: 'Starting playback...'
Debug: MplayerProcess::parseLine: 'VDec: vo config request - 640 x 360 (preferred colorspace: Planar YV12)'
Debug: MplayerProcess::parseLine: 'VDec: using Planar YV12 as output csp (no 0)'
Debug: MplayerProcess::parseLine: 'Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.'
Debug: MplayerProcess::parseLine: md.video_aspect set to 1.780000
Debug: MplayerProcess::parseLine: 'ID_VIDEO_ASPECT=1.7778'
Debug: MplayerProcess::parseLine: md.video_aspect set to 1.777800
Debug: MplayerProcess::parseLine: '[swscaler @ 0x8934890]SwScaler: using unscaled yuv420p -> bgr24 special converter'
Debug: MplayerProcess::parseLine: 'VO: [x11] 640x360 => 640x360 Planar YV12  [zoom]'
Debug: Core::gotVO: 'x11'
Debug: Core::gotWindowResolution: 640, 360
Debug: BaseGuiPlus::resizeWindow: 640, 360
Debug: BaseGui::resizeWindow: 640, 360
Debug: BaseGui::resizeWindow: size to scale: 640, 360
Debug: BaseGui::resizeWindow: done: window size: 640, 491
Debug: BaseGui::resizeWindow: done: panel->size: 640, 360
Debug: BaseGui::resizeWindow: done: mplayerwindow->size: 640, 360
Debug: MplayerProcess::parseLine: 'X11 error: BadAccess during XSelectInput Call'
Debug: MplayerProcess::parseLine: 'X11 error: The 'ButtonPressMask' mask of specified window has probably already used by another appication (see man XSelectInput)'
Debug: MplayerProcess::parseLine: 'X11 error: MPlayer discards mouse control (reconfiguring)'
Debug: MplayerProcess::parseLine: 'X11 error: BadAccess during XSelectInput Call'
Debug: MplayerProcess::parseLine: 'X11 error: The 'ButtonPressMask' mask of specified window has probably already used by another appication (see man XSelectInput)'
Debug: MplayerProcess::parseLine: 'X11 error: MPlayer discards mouse control (reconfiguring)'
Debug: MplayerProcess::parseLine: starting sec: 52.700000
Debug: Core::gotStartingTime: 52.700000
Debug: Core::gotStartingTime: current_sec: 48.700000
Debug: Core::finishRestart
Debug: Core::newMediaPlaying
Debug: Core::initializeMenus
Debug: BaseGui::initializeMenus
Debug: MediaData::list
Debug:   filename: '/media/sda3/Film/Factory Girl/factory_girl-2006-dvdrip-en.avi'
Debug:   duration: 5742.560000
Debug:   video_width: 640
Debug:   video_height: 360
Debug:   video_aspect: 1.777800
Debug:   type: 0
Debug:   novideo: 0
Debug:   dvd_id: ''
Debug:   initialized: 1
Debug:   mkv_chapters: 0
Debug:   Subs:
Debug:   Audios:
Debug:     item # 0
Debug:      ID: '1' lang: '' name: ''
Debug:      filename: '' duration: 0.000000 chapters: 0 angles: 0
Debug:   Titles:
Debug:   demuxer: 'avi'
Debug:   video_format: 'DX50'
Debug:   audio_format: '85'
Debug:   video_bitrate: 765216
Debug:   video_fps: '25.000'
Debug:   audio_bitrate: 128000
Debug:   audio_rate: 44100
Debug:   audio_nch: 2
Debug:   video_codec: 'ffodivx'
Debug:   audio_codec: 'mad'
Debug: MediaSettings::list
Debug:   current_sec: 48.700000
Debug:   current_sub_id: 90000
Debug:   current_audio_id: 1
Debug:   current_title_id: -1000
Debug:   current_chapter_id: -1000
Debug:   current_angle_id: -1000
Debug:   aspect_ratio_id: 1
Debug:   volume: 100
Debug:   mute: 0
Debug:   external_subtitles: ''
Debug:   external_audio: ''
Debug:   sub_delay: 0
Debug:   audio_delay: 0
Debug:   sub_pos: 100
Debug:   sub_scale: 5.000000
Debug:   sub_scale_***: 1.000000
Debug:   brightness: 0
Debug:   contrast: 0
Debug:   gamma: 0
Debug:   hue: 0
Debug:   saturation: 0
Debug:   speed: 1.000000
Debug:   phase_filter: 0
Debug:   current_denoiser: 0
Debug:   deblock_filter: 0
Debug:   dering_filter: 0
Debug:   noise_filter: 0
Debug:   postprocessing_filter: 0
Debug:   upscaling_filter: 0
Debug:   current_deinterlacer: 0
Debug:   add_letterbox: 0
Debug:   karaoke_filter: 0
Debug:   extrastereo_filter: 0
Debug:   volnorm_filter: 0
Debug:   audio_use_channels: 2
Debug:   stereo_mode: 0
Debug:   panscan_factor: 1.000000
Debug:   flip: 0
Debug:   forced_demuxer: ''
Debug:   forced_video_codec: ''
Debug:   forced_audio_codec: ''
Debug:   original_demuxer: ''
Debug:   original_video_codec: ''
Debug:   original_audio_codec: ''
Debug:   mplayer_additional_options: ''
Debug:   mplayer_additional_video_filters: ''
Debug:   mplayer_additional_audio_filters: ''
Debug:   win_width: 640
Debug:   win_height: 360
Debug:   win_aspect(): 1.777778
Debug:   starting_time: 0.100000
Debug:   is264andHD: 0
Debug: Core::changeSubtitle: 90000
Debug: Core::changeSubtitle: ID: -1
Debug: MplayerVersion::isMplayerAtLeast: comparing 25158 with 24722
Debug: Core::tellmp: 'sub_select -1'
Debug: Core::updateWidgets
Debug: DefaultGui::updateWidgets
Debug: BaseGui::updateWidgets
Debug: Core::changeAspectRatio: 1
Debug: Core::changeAspectRatio: mset.win_width 640, mset.win_height: 360
Debug: Core::setVolume: 100
Debug: Core::tellmp: 'volume 100 1'
Debug: Core::updateWidgets
Debug: DefaultGui::updateWidgets
Debug: BaseGui::updateWidgets
Debug: Core::displayMessage
Debug: Core::setVolume: 100
Debug: Core::setVolume: 100
Debug: Core::setVolume: 100
Debug: Core::setGamma: 0
Debug: Core::tellmp: 'gamma 0 1'
Debug: Core::displayMessage
Debug: Core::changePanscan: 1.000000
Debug: Core::displayMessage
Debug: Core::autosaveMplayerLog
Debug: Core::checkIfVideoIsHD
Debug: DefaultGui::enableActionsOnPlaying
Debug: BaseGui::enableActionsOnPlaying
Debug: BaseGui::newMediaLoaded
Debug: Recents::add: '/media/sda3/Film/Factory Girl/factory_girl-2006-dvdrip-en.avi'
Debug: BaseGui::updateRecents
Debug: Playlist:: getMediaInfo
Debug: name: 'factory_girl-2006-dvdrip-en.avi'
Debug: BaseGuiPlus::updateMediaInfo
Debug: BaseGui::updateMediaInfo
Debug: Core::updateWidgets
Debug: DefaultGui::updateWidgets
Debug: BaseGui::updateWidgets
Debug: BaseGui::displayState: Playing
Debug: mplayer reports that now it's playing
Debug: BaseGui::toggleFullscreen: 1
Debug: BaseGui::toggleFullscreen: was_maximized: 0
Debug: DefaultGui::aboutToEnterFullscreen
Debug: BaseGuiPlus::aboutToEnterFullscreen
Debug: DefaultGui::updateWidgets
Debug: BaseGui::updateWidgets
Debug: MplayerProcess::parseLine: 'Invalid command for bound key f : invalid_command             '
Debug: BaseGui::toggleFullscreen: 0
Debug: DefaultGui::aboutToExitFullscreen
Debug: BaseGuiPlus::aboutToExitFullscreen
Debug: DefaultGui::updateWidgets
Debug: BaseGui::updateWidgets
Debug: BaseGui::toggleFullscreen: 0
Debug: BaseGui::toggleFullscreen: nothing to do, returning
Debug: MplayerProcess::parseLine: ''
Debug: MplayerProcess::parseLine: ''
Debug: MplayerProcess::parseLine: '           ************************************************'
Debug: MplayerProcess::parseLine: '           **** Your system is too SLOW to play this!  ****'
Debug: MplayerProcess::parseLine: '           ************************************************'
Debug: MplayerProcess::parseLine: ''
Debug: MplayerProcess::parseLine: 'Possible reasons, problems, workarounds:'
Debug: MplayerProcess::parseLine: '- Most common: broken/buggy _audio_ driver'
Debug: MplayerProcess::parseLine: '  - Try -ao sdl or use the OSS emulation of ALSA.'
Debug: MplayerProcess::parseLine: '  - Experiment with different values for -autosync, 30 is a good start.'
Debug: MplayerProcess::parseLine: '- Slow video output'


Debug: MplayerProcess::parseLine: '  - Try a different -vo driver (-vo help for a list) or try -framedrop!'
Debug: MplayerProcess::parseLine: '- Slow CPU'
Debug: MplayerProcess::parseLine: '  - Don't try to play a big DVD/DivX on a slow CPU! Try some of the lavdopts,'
Debug: MplayerProcess::parseLine: '    e.g. -vfm ffmpeg -lavdopts lowres=1:fast:skiploopfilter=all.'
Debug: MplayerProcess::parseLine: '- Broken file'
Debug: MplayerProcess::parseLine: '  - Try various combinations of -nobps -ni -forceidx -mc 0.'
Debug: MplayerProcess::parseLine: '- Slow media (NFS/SMB mounts, DVD, VCD etc)'
Debug: MplayerProcess::parseLine: '  - Try -cache 8192.'
Debug: MplayerProcess::parseLine: '- Are you using -cache to play a non-interleaved AVI file?'
Debug: MplayerProcess::parseLine: '  - Try -nocache.'
Debug: MplayerProcess::parseLine: 'Read DOCS/HTML/en/video.html for tuning/speedup tips.'
Debug: MplayerProcess::parseLine: 'If none of this helps you, read DOCS/HTML/en/bugreports.html.'
Debug: MplayerProcess::parseLine: ''

---

### Post by primlinOS on 2008-05-24
This works for me ... cheers!

> Had the same problem but it's solved now. I have an inspiron 9400 with mobility radeon 1400. Here are the steps:
1. Uninstall xserv-xgl
2. Uninstal all compiz related packages
3. Install envyNG
4. Restart
5. Install ati driver through envyNG
6. Install compiz
7. System -> Hardware admin -> enable ati driver[/B]

---

### Post by primlinOS on 2008-05-26
Actually, let me just say, doing the above solves some major problems, but creates a slew of minor ones. Turns out, for me, there are some serious problems running compiz, and it has to be turned off -- the number of issues is difficult to list.  After turning it off, mplayer breaks -- due to some very weird synch problems with audio/video; which could be settings in preferences.  However, vlc is working, except fullscreen mode keeps the top panel visible -- which is a bug that is common (apparently) when using Kubuntu, though I am using gnome.  Anyway, if you move the panel to the right hand side fullscreen works, if you move it to the left, it does not.   Anyway, problems problems problems -- Gutsy was much more stable for me in almost every way (except firefox, which was always unstable and is still unstable).  I really hope some of this stuff gets fixed via auto updates, but even so, ubuntu is (r)evolution!

---

### Post by caiooiac on 2008-07-15
Any suggestions for the same problem with a nvidia board?

Thanks

---

### Post by ragip on 2008-09-12
I have the same problem on my Fujitsu Siemens Amilo v2045. It has got an ATI Radeon Mobility x300 on it and produces bad quality, flickering video. I'll tweak with the drivers, etc and (hope to) talk about results soon.
Thanks to everyone for the support :)

---

### Post by hamidoo on 2009-04-29
Hi guys,
I also found most videos in totem movie player pixelated.
I tried SMPlayer which includes a post-processing option and it rocks!
i totally converted to it now

---

