---
title: "Smplayer"
date: 2008-03-30
forum: Multimedia &amp; Video
---

### Post by Maurice08 on 2008-03-30
I have installed smplayer, none of the the keyboard controls work but seeking using the scroll wheel does!

Can anyone help.

Thanks
Maurice08
Also all the toolbar controls are greyed out!

---

### Post by xc3RnbFO8P on 2008-03-30
Try this thread>
[http://ubuntuforums.org/showthread.php?t=684193&page=3]("http://ubuntuforums.org/showthread.php?t=684193&page=3")

---

### Post by rvm4000 on 2008-03-30
> **Maurice08 said:**
> I have installed smplayer, none of the the keyboard controls work but seeking using the scroll wheel does!

Can anyone help.

Thanks
Maurice08
Also all the toolbar controls are greyed out!

Most "actions" are disabled until a file start to play. It seems in your case,  for some reason, smplayer doesn't realize that the file has begun to play.

Could you take a look at the mplayer log (options->view logs) when you play a file, and copy it here?

---

### Post by Maurice08 on 2008-03-31
Here is mplayer log:-

/usr/bin/mplayer -noquiet -nofs -sub-fuzziness 1 -identify -slave -vo xv, -zoom -nokeepaspect -framedrop -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 39845902 -monitorpixelaspect 1 -subfont-autoscale 1 -subfont-text-scale 5 -subcp ISO-8859-1 -subpos 100 -contrast 0 -brightness 0 -hue 0 -saturation 0 -nocache -osdlevel 0 -vf-add screenshot -channels 2 -af scaletempo /home/paul/Videos/mix.wmv

MPlayer dev-SVN-r25873-4.1.2 (C) 2000-2008 MPlayer Team
CPU: AMD Athlon(tm) XP 2500+ (Family: 6, Model: 10, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Terminal type `unknown' is not defined.
ID_AUDIO_ID=1
ID_VIDEO_ID=2
ID_FILENAME=/home/paul/Videos/mix.wmv
ID_DEMUXER=asf
ID_VIDEO_FORMAT=WMV3
ID_VIDEO_BITRATE=436000
ID_VIDEO_WIDTH=384
ID_VIDEO_HEIGHT=216
ID_VIDEO_FPS=1000.000
ID_VIDEO_ASPECT=0.0000
ID_AUDIO_FORMAT=353
ID_AUDIO_BITRATE=0
ID_AUDIO_RATE=0
ID_AUDIO_NCH=0
ID_LENGTH=1132.00
DMO dll supports VO Optimizations 0 1
DMO dll might use previous sample when requested
GetOutput r=0x0   size:248832  align:1
StreamCount r=0x0  1  1
Decoder supports the following formats: YV12 YUY2 UYVY YVYU RGB8 RGB555 RGB565 RGB24 [swscaler @ 0x8a07708]No accelerated colorspace conversion found
[swscaler @ 0x8a07708]SwScaler: using unscaled yuv420p -> rgb24 special converter
RGB32 
Decoder is capable of YUV output (flags 0x1b)
ID_VIDEO_CODEC=wmv9dmo
ID_AUDIO_BITRATE=64000
ID_AUDIO_RATE=44100
ID_AUDIO_NCH=2
ID_AUDIO_CODEC=ffwmav2

---

### Post by Maurice08 on 2008-03-31
Here is smplayer log also for your info

main: lock_file: /home/paul/.smplayer/smplayer_init.lock
global_init
global_init: config file: '/home/paul/.smplayer/smplayer.ini'
Preferences:load
Translator::loadCatalog: can't load qt_en_GB from /usr/share/smplayer/translations
Translator::loadCatalog: can't load qt_en_GB from /usr/share/qt4/translations
Translator::loadCatalog: can't load smplayer_en_GB from /usr/share/smplayer/translations
This is SMPlayer v. 0.6.0rc3 (SVN r1000) running on Linux
Qt v. 4.2.3
 * application path: '/usr/bin'
 * data path: '/usr/share/smplayer'
 * translation path: '/usr/share/smplayer/translations'
 * doc path: '/usr/share/doc/smplayer'
 * themes path: '/usr/share/smplayer/themes'
 * shortcuts path: '/usr/share/smplayer/shortcuts'
 * smplayer home path: '/home/paul/.smplayer'
 * ini path: '/home/paul/.smplayer'
 * current path: '/home/paul'
SMPlayer::processArgs: arguments: 2
SMPlayer::processArgs: 0 = smplayer
SMPlayer::processArgs: 1 = /home/paul/Videos/mix.wmv
SMPlayer::processArgs: files_to_play: count: 1
SMPlayer::processArgs: files_to_play[0]: '/home/paul/Videos/mix.wmv'
Recents::load
Core::Core: file_settings: '/home/paul/.smplayer/smplayer_files.ini'
MplayerProcess::init_rx
MplayerLayer::allowClearingBackground: 0
Preferences::monitor_aspect_double
 warning: monitor_aspect couldn't be parsed!
 monitor_aspect set to 0
Playlist::setModified: 0
Playlist::loadSettings
Playlist::addItem: '/home/paul/Videos/mix.wmv'
Playlist::setModified: 0
name: 'mix.wmv'
Style name: 'cleanlooks'
Style class name: 'QCleanlooksStyle'
BaseGui::initializeMenus
BaseGui::initializeMenus
BaseGui::updateRecents
BaseGui::updateWidgets
BaseGui::updateWidgets
BaseGui::updateRecents
PlaylistDock::hideEvent: isFloating: 0
 undocked
PlaylistDock::showEvent: isFloating: 1
PlaylistDock::hideEvent: isFloating: 1
BaseGui::initializeMenus
BaseGui::updateRecents
BaseGui::updateWidgets
BaseGuiPlus::loadConfig
DefaultGui::createStatusBar
DefaultGui::createActions
DefaultGui::createControlWidget
TimeSlider::setDragDelay: 100
DefaultGui::createControlWidgetMini
TimeSlider::setDragDelay: 100
TimeSlider::setDragDelay: 100
BaseGui::initializeMenus
BaseGui::updateRecents
DefaultGui::updateWidgets
BaseGui::updateWidgets
DefaultGui::loadConfig
DefaultGui::updateWidgets
BaseGui::updateWidgets
SMPlayer::gui: changed working directory to app path
SMPlayer::gui: current directory: /usr/bin
BaseGui::showEvent
BaseGui::openFiles
Playlist::setModified: 0
Playlist::addFiles
Playlist::addItem: '/home/paul/Videos/mix.wmv'
name: 'mix.wmv'
 * latest_dir: ''
BaseGui::open: '/home/paul/Videos/mix.wmv'
Core::open: '/home/paul/Videos/mix.wmv'
 * identified as local file
Core::openFile: '/home/paul/Videos/mix.wmv'
Core::playNewFile: '/home/paul/Videos/mix.wmv'
Core::saveMediaInfo
Core::checkHaveSettingsSaved: group_name: '_home_paul_Videos_mix_wmv_71189296'
We have settings for this file!!!
Core::loadMediaInfo: '_home_paul_Videos_mix_wmv_71189296'
MediaSettings::load
Media settings read
Core::playNewFile: volume: 40, old_volume: 40
Core::initPlaying
Core::startMplayer
Core::startMplayer: setting working directory to '/home/paul/.smplayer/screenshots'
Core::startMplayer: * not using -colorkey for 
Core::startMplayer: * report if you can't see the video
MplayerVersion::isMplayerAtLeast: comparing 24924 with 25873
Core::startMplayer: command: '/usr/bin/mplayer -noquiet -nofs -sub-fuzziness 1 -identify -slave -vo xv, -zoom -nokeepaspect -framedrop -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 39845902 -monitorpixelaspect 1 -subfont-autoscale 1 -subfont-text-scale 5 -subcp ISO-8859-1 -subpos 100 -contrast 0 -brightness 0 -hue 0 -saturation 0 -nocache -osdlevel 0 -vf-add screenshot -channels 2 -af scaletempo /home/paul/Videos/mix.wmv'
MplayerLayer::playingStarted
BaseGui::calculateDiff: diff_size: 0, 0
BaseGui::calculateDiff: diff_size set to: 0, 100
MplayerProcess::init_rx
main: removing /home/paul/.smplayer/smplayer_init.lock
BaseGui::loadActions
ActionsEditor::loadFromConfig
BaseGui::initializeMenus
BaseGui::updateRecents
DefaultGui::updateWidgets
BaseGui::updateWidgets
MplayerProcess::parseLine: 'MPlayer dev-SVN-r25873-4.1.2 (C) 2000-2008 MPlayer Team'
MplayerVersion::mplayerVersion: MPlayer SVN revision found: 25873
MplayerProcess::parseLine: MPlayer SVN: 25873
MplayerProcess::parseLine: 'CPU: AMD Athlon(tm) XP 2500+ (Family: 6, Model: 10, Stepping: 0)'
MplayerProcess::parseLine: 'CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0'
MplayerProcess::parseLine: 'Compiled with runtime CPU detection.'
MplayerProcess::parseLine: 'mplayer: could not connect to socket'
MplayerProcess::parseLine: 'mplayer: No such file or directory'
MplayerProcess::parseLine: 'Terminal type `unknown' is not defined.'
MplayerProcess::parseLine: 'ID_AUDIO_ID=1'
MplayerProcess::parseLine: ID_AUDIO_ID: 1
MplayerProcess::parseLine: 'ID_VIDEO_ID=2'
MplayerProcess::parseLine: 'ID_FILENAME=/home/paul/Videos/mix.wmv'
MplayerProcess::parseLine: 'ID_DEMUXER=asf'
MplayerProcess::parseLine: 'ID_VIDEO_FORMAT=WMV3'
MplayerProcess::parseLine: 'ID_VIDEO_BITRATE=436000'
MplayerProcess::parseLine: 'ID_VIDEO_WIDTH=384'
MplayerProcess::parseLine: md.video_width set to 384
MplayerProcess::parseLine: 'ID_VIDEO_HEIGHT=216'
MplayerProcess::parseLine: md.video_height set to 216
MplayerProcess::parseLine: 'ID_VIDEO_FPS=1000.000'
MplayerProcess::parseLine: 'ID_VIDEO_ASPECT=0.0000'
MplayerProcess::parseLine: md.video_aspect set to 1.777778
MplayerProcess::parseLine: 'ID_AUDIO_FORMAT=353'
MplayerProcess::parseLine: 'ID_AUDIO_BITRATE=0'
MplayerProcess::parseLine: 'ID_AUDIO_RATE=0'
MplayerProcess::parseLine: 'ID_AUDIO_NCH=0'
MplayerProcess::parseLine: 'ID_LENGTH=1132.00'
MplayerProcess::parseLine: md.duration set to 1132.000000
MplayerProcess::parseLine: 'DMO dll supports VO Optimizations 0 1'
MplayerProcess::parseLine: 'DMO dll might use previous sample when requested'
MplayerProcess::parseLine: 'GetOutput r=0x0   size:248832  align:1'
MplayerProcess::parseLine: 'StreamCount r=0x0  1  1'
MplayerProcess::parseLine: 'Decoder supports the following formats: YV12 YUY2 UYVY YVYU RGB8 RGB555 RGB565 RGB24 [swscaler @ 0x8a07708]No accelerated colorspace conversion found'
MplayerProcess::parseLine: '[swscaler @ 0x8a07708]SwScaler: using unscaled yuv420p -> rgb24 special converter'
MplayerProcess::parseLine: 'RGB32 '
MplayerProcess::parseLine: 'Decoder is capable of YUV output (flags 0x1b)'
MplayerProcess::parseLine: 'ID_VIDEO_CODEC=wmv9dmo'
MplayerProcess::parseLine: 'ID_AUDIO_BITRATE=64000'
MplayerProcess::parseLine: 'ID_AUDIO_RATE=44100'
MplayerProcess::parseLine: 'ID_AUDIO_NCH=2'
MplayerProcess::parseLine: 'ID_AUDIO_CODEC=ffwmav2'
BaseGui::showLog

---

### Post by rvm4000 on 2008-03-31
The output of your mplayer really lacks a lot of info. Compare with mine:
> 
MPlayer dev-SVN-r26264-3.4.5 (C) 2000-2008 MPlayer Team
CPU: AMD Turion(tm) 64 Mobile Technology MK-36 (Family: 15, Model: 76, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx SSE SSE2
Setting process priority: abovenormal
C:\WINDOWS\Fonts\arialbd.ttf doesn't look like a bitmap font description, ignoring.
Cannot load bitmap font: C:\WINDOWS\Fonts\arialbd.ttf

Playing video.flv.
libavformat file format detected.
ID_VIDEO_ID=0
[lavf] Video stream found, -vid 0
ID_AUDIO_ID=1
[lavf] Audio stream found, -aid 1
VIDEO:  [FLV1]  320x240  0bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
ID_FILENAME=video.flv
ID_DEMUXER=lavfpref
ID_VIDEO_FORMAT=FLV1
ID_VIDEO_BITRATE=0
ID_VIDEO_WIDTH=320
ID_VIDEO_HEIGHT=240
ID_VIDEO_FPS=29.970
ID_VIDEO_ASPECT=0.0000
ID_AUDIO_FORMAT=85
ID_AUDIO_BITRATE=64000
ID_AUDIO_RATE=22050
ID_AUDIO_NCH=1
ID_LENGTH=119.99
ID_SEEKABLE=1
Opening video filter: [screenshot]
Opening video filter: [***]
[***] Init
[***] Updating font cache.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffflv] vfm: ffmpeg (FFmpeg Flash video)
==========================================================================
ID_VIDEO_CODEC=ffflv
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 22050 Hz, 2 ch, s16le, 8.0 kbit/1.13% (ratio: 1000->88200)
ID_AUDIO_BITRATE=8000
ID_AUDIO_RATE=22050
ID_AUDIO_NCH=2
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [dsound] 22050Hz 2ch s16le (2 bytes per sample)
ID_AUDIO_CODEC=mp3
Starting playback...
VDec: vo config request - 320 x 240 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
[swscaler @ 00C0B6F4]No accelerated colorspace conversion found
[swscaler @ 00C0B6F4]using unscaled yuv420p -> rgb24 special converter
VO: [directx] 320x240 => 320x240 Planar YV12  [zoom]

Exiting... (Quit)

Do you have something in your ~/.mplayer/config (or /etc/mplayer)? I guess there should be some option there which makes mplayer to not display all info.

---

### Post by Maurice08 on 2008-03-31
rvm 4000 thanks for your input. Don't know what the problem was but having uninstalled mplayer, smplayer and deleted all directories I could find with those names, I have installed your latest versions of both players from the .deb files. 

Everything now appears to work as it should

---

