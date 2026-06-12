---
title: "smplayer doesn't play the same as mplayer"
date: 2010-12-26
forum: Multimedia Software
---

### Post by pickarooney on 2010-12-26
Today I wanted to ready some 3gp files so had to install the w32codecs and mplayer version from the medibuntu repository. Now I can play back these files perfectly with mplayer from teh command line but when I open them with smplayer there is no video, just (choppy) sound. Xine also plays them back now although it didn't before. I know the first time I ran smplayer on this installation I had to choose which version of mplayer it was running with but don't know if I can do this again to tell it to use the installed medibuntu mplayer. 

I'm at a bit of a loss as to why the front-end smplayer would not simply play files with the exact same results as mplayer from the CLI. I haven't rebooted since, but don't imagine that would make much difference.

---

### Post by andrew.46 on 2010-12-27
Hi pickarooney,

Have you had a look at the logs that SMPlayer generates during playback? These can be seen in SMPlayer from Options --> View Logs and should give an indication as to what is going wrong. You can alter the path to the MPlayer executable from Options --> Preferences --> General --> Mplayer Executable.

Andrew

---

### Post by pickarooney on 2010-12-28
The log doesn't tell me a whole lot. The path to mplayer is correct (/usr/bin/mplayer). Rebooting didn't fix the problem.

```
[20:02:42:885] main: lock_file: /home/richard/.config/smplayer/smplayer_init.lock
[20:02:42:886] global_init
[20:02:42:886] global_init: config file: '/home/richard/.config/smplayer/smplayer.ini'
[20:02:42:886] Preferences::load
[20:02:42:887] AssStyles::load
[20:02:42:887] Translator::loadCatalog: can't load qt_en_IE from /usr/share/smplayer/translations
[20:02:42:887] Translator::loadCatalog: can't load qt_en_IE from /usr/share/qt4/translations
[20:02:42:887] Translator::loadCatalog: can't load smplayer_en_IE from /usr/share/smplayer/translations
[20:02:42:888] This is SMPlayer v. 0.6.9 (SVN r3447) running on Linux
[20:02:42:888] Compiled with Qt v. 4.6.2, using 4.7.0
[20:02:42:888]  * application path: '/usr/bin'
[20:02:42:888]  * data path: '/usr/share/smplayer'
[20:02:42:888]  * translation path: '/usr/share/smplayer/translations'
[20:02:42:888]  * doc path: '/usr/share/doc/smplayer'
[20:02:42:888]  * themes path: '/usr/share/smplayer/themes'
[20:02:42:888]  * shortcuts path: '/usr/share/smplayer/shortcuts'
[20:02:42:888]  * config path: '/home/richard/.config/smplayer'
[20:02:42:888]  * ini path: '/home/richard/.config/smplayer'
[20:02:42:888]  * file for subtitles' styles: '/home/richard/.config/smplayer/styles.***'
[20:02:42:888]  * current path: '/home/richard/.config'
[20:02:42:888] SMPlayer::processArgs: arguments: 2
[20:02:42:888] SMPlayer::processArgs: 0 = smplayer
[20:02:42:888] SMPlayer::processArgs: 1 = 
[20:02:42:888] SMPlayer::processArgs: files_to_play: count: 1
[20:02:42:888] SMPlayer::processArgs: files_to_play[0]: ''
[20:02:42:888] MyClient::MyClient
[20:02:42:888] SMPlayer::processArgs: trying to connect to port 44872
[20:02:42:888] SMPlayer::gui: changed working directory to app path
[20:02:42:889] SMPlayer::gui: current directory: /usr/bin
[20:02:42:889] Screen::setAutoHideCursor: 0
[20:02:42:889] Screen::setAutoHideCursor: 0
[20:02:43:109] Core::changeFileSettingsMethod: normal
[20:02:43:139] MplayerLayer::setRepaintBackground: 0
[20:02:43:139] Preferences::monitor_aspect_double
[20:02:43:139]  warning: monitor_aspect couldn't be parsed!
[20:02:43:139]  monitor_aspect set to 0
[20:02:43:179] Playlist::setModified: 0
[20:02:43:192] Playlist::loadSettings
[20:02:43:193] Playlist::addItem: '/home/richard/Pictures/Kids/StephensDay2010/video-2010-12-26-13-42-18.mp4'
[20:02:43:193] Playlist::setModified: 0
[20:02:43:193] Playlist::updateView
[20:02:43:193] Playlist::updateView: name: 'video-2010-12-26-13-42-18.mp4'
[20:02:43:201] Style name: 'gtk+'
[20:02:43:201] Style class name: 'QGtkStyle'
[20:02:43:280] Favorites::load
[20:02:43:281] TVList::parse_channels_conf
[20:02:43:281] VList::parse_channels_conf: /home/richard/.mplayer/channels.conf.ter doesn't exist
[20:02:43:281] TVList::parse_channels_conf: can't open /home/richard/.mplayer/channels.conf
[20:02:43:281] Favorites::load
[20:02:43:281] TVList::parse_channels_conf
[20:02:43:281] VList::parse_channels_conf: /home/richard/.mplayer/channels.conf.ter doesn't exist
[20:02:43:281] TVList::parse_channels_conf: can't open /home/richard/.mplayer/channels.conf
[20:02:43:293] BaseGui::initializeMenus
[20:02:43:331] BaseGui::initializeMenus
[20:02:43:331] BaseGui::updateRecents
[20:02:43:331] BaseGui::updateWidgets
[20:02:43:331] Core::changeUseAss: 1
[20:02:43:331] Core::changeSubVisilibity: 1
[20:02:43:331] Core::tellmp: 'sub_visibility 1'
[20:02:43:332] WARNING:  tellmp: no process running: sub_visibility 1
[20:02:43:332] Core::displayMessage
[20:02:43:332] BaseGui::setStayOnTop: 0
[20:02:43:332] BaseGui::setStayOnTop: nothing to do
[20:02:43:332] BaseGui::updateWidgets
[20:02:43:332] BaseGui::updateRecents
[20:02:43:333] Preferences::save
[20:02:43:333] AssStyles::save
[20:02:43:337] BaseGui::initializeGui: server running on port 41463
[20:02:43:355] BaseGui::initializeMenus
[20:02:43:355] BaseGui::updateRecents
[20:02:43:356] BaseGui::updateWidgets
[20:02:43:357] BaseGuiPlus::loadConfig
[20:02:43:357] DefaultGui::createStatusBar
[20:02:43:358] DefaultGui::createActions
[20:02:43:358] DefaultGui::createControlWidget
[20:02:43:358] DefaultGui::createControlWidgetMini
[20:02:43:374] BaseGui::initializeMenus
[20:02:43:374] BaseGui::updateRecents
[20:02:43:374] DefaultGui::updateWidgets
[20:02:43:374] BaseGui::updateWidgets
[20:02:43:375] DefaultGui::loadConfig
[20:02:43:375] DesktopInfo::isInsideScreen: geometry of screen: x:0 y:0 w:1920 h:1080
[20:02:43:375] ToolbarEditor::load: 'toolbar1'
[20:02:43:375] ToolbarEditor::load: loading action open_file
[20:02:43:376] ToolbarEditor::load: loading action open_dvd
[20:02:43:376] ToolbarEditor::load: loading action open_url
[20:02:43:376] ToolbarEditor::load: loading action separator
[20:02:43:376] ToolbarEditor::load: adding separator
[20:02:43:376] ToolbarEditor::load: loading action compact
[20:02:43:376] ToolbarEditor::load: loading action fullscreen
[20:02:43:376] ToolbarEditor::load: loading action separator
[20:02:43:376] ToolbarEditor::load: adding separator
[20:02:43:376] ToolbarEditor::load: loading action screenshot
[20:02:43:376] ToolbarEditor::load: loading action separator
[20:02:43:376] ToolbarEditor::load: adding separator
[20:02:43:376] ToolbarEditor::load: loading action show_file_properties
[20:02:43:376] ToolbarEditor::load: loading action show_playlist
[20:02:43:376] ToolbarEditor::load: loading action show_preferences
[20:02:43:376] ToolbarEditor::load: loading action separator
[20:02:43:376] ToolbarEditor::load: adding separator
[20:02:43:376] ToolbarEditor::load: loading action play_prev
[20:02:43:376] ToolbarEditor::load: loading action play_next
[20:02:43:376] ToolbarEditor::load: 'controlwidget'
[20:02:43:376] ToolbarEditor::load: loading action play
[20:02:43:376] ToolbarEditor::load: loading action pause_and_frame_step
[20:02:43:376] ToolbarEditor::load: loading action stop
[20:02:43:377] ToolbarEditor::load: loading action separator
[20:02:43:377] ToolbarEditor::load: adding separator
[20:02:43:377] ToolbarEditor::load: loading action rewindbutton_action
[20:02:43:377] ToolbarEditor::load: loading action timeslider_action
[20:02:43:377] TimeSlider::setDragDelay: 100
[20:02:43:377] ToolbarEditor::load: loading action forwardbutton_action
[20:02:43:377] ToolbarEditor::load: loading action separator
[20:02:43:377] ToolbarEditor::load: adding separator
[20:02:43:377] ToolbarEditor::load: loading action fullscreen
[20:02:43:377] ToolbarEditor::load: loading action mute
[20:02:43:377] ToolbarEditor::load: loading action volumeslider_action
[20:02:43:377] ToolbarEditor::load: 'controlwidget_mini'
[20:02:43:377] ToolbarEditor::load: loading action play_or_pause
[20:02:43:377] ToolbarEditor::load: loading action stop
[20:02:43:377] ToolbarEditor::load: loading action separator
[20:02:43:377] ToolbarEditor::load: adding separator
[20:02:43:377] ToolbarEditor::load: loading action rewind1
[20:02:43:377] ToolbarEditor::load: loading action timeslider_action
[20:02:43:377] TimeSlider::setDragDelay: 100
[20:02:43:377] ToolbarEditor::load: loading action forward1
[20:02:43:378] ToolbarEditor::load: loading action separator
[20:02:43:378] ToolbarEditor::load: adding separator
[20:02:43:378] ToolbarEditor::load: loading action mute
[20:02:43:378] ToolbarEditor::load: loading action volumeslider_action
[20:02:43:378] ToolbarEditor::load: ''
[20:02:43:378] ToolbarEditor::load: loading action play
[20:02:43:378] ToolbarEditor::load: loading action pause
[20:02:43:378] ToolbarEditor::load: loading action stop
[20:02:43:378] ToolbarEditor::load: loading action separator
[20:02:43:378] ToolbarEditor::load: adding separator
[20:02:43:378] ToolbarEditor::load: loading action rewindbutton_action
[20:02:43:378] ToolbarEditor::load: loading action timeslider_action
[20:02:43:378] TimeSlider::setDragDelay: 100
[20:02:43:378] ToolbarEditor::load: loading action forwardbutton_action
[20:02:43:378] ToolbarEditor::load: loading action separator
[20:02:43:378] ToolbarEditor::load: adding separator
[20:02:43:378] ToolbarEditor::load: loading action fullscreen
[20:02:43:378] ToolbarEditor::load: loading action mute
[20:02:43:378] ToolbarEditor::load: loading action volumeslider_action
[20:02:43:379] ToolbarEditor::load: loading action separator
[20:02:43:379] ToolbarEditor::load: adding separator
[20:02:43:379] ToolbarEditor::load: loading action timelabel_action
[20:02:43:379] Helper::qtVersion: 4700
[20:02:43:381] DefaultGui::loadConfig: playlist visible: 0
[20:02:43:381] DefaultGui::loadConfig: playlist position: 0, 0
[20:02:43:381] DefaultGui::loadConfig: playlist size: 100 x 30
[20:02:43:381] DefaultGui::updateWidgets
[20:02:43:381] BaseGui::updateWidgets
[20:02:43:383] BaseGui::showEvent
[20:02:43:385] BaseGui::openFiles
[20:02:43:385] Playlist::setModified: 0
[20:02:43:385] Playlist::addFiles
[20:02:43:393] Playlist::addItem: ''
[20:02:43:393] Playlist::updateView
[20:02:43:393] Playlist::updateView: name: ''
[20:02:43:394] Playlist::addFiles: latest_dir: '/home/richard/Pictures/Kids/StephensDay2010'
[20:02:43:394] BaseGui::open: ''
[20:02:43:394] Core::open: ''
[20:02:43:394] Core::open: * not identified, playing as stream
[20:02:43:394] Core::openStream: ''
[20:02:43:394] Core::saveMediaInfo
[20:02:43:394] Core::initPlaying
[20:02:43:394] Core::startMplayer
[20:02:43:394] WARNING: Core:startMplayer: file is empty!
[20:02:43:394] main: remove_lock: /home/richard/.config/smplayer/smplayer_init.lock
[20:02:43:405] BaseGui::loadActions
[20:02:43:405] ActionsEditor::loadFromConfig
[20:02:43:917] BaseGui::initializeMenus
[20:02:43:917] BaseGui::updateRecents
[20:02:43:918] DefaultGui::updateWidgets
[20:02:43:918] BaseGui::updateWidgets
[20:02:47:690] BaseGui::showLog

```

---

### Post by andrew.46 on 2010-12-28
I guess the interesting log would be the MPlayer one from within SMPlayer on the file that fails to play correctly. Can you give the *full* log of this as well?

Andrew

---

### Post by pickarooney on 2010-12-28
There's not a whole lot more in this either, but I've now foudn something which possibly explains part of this. 

I tried vlc, xine and mplayer and all play the file fine. kmplayer doesn't play it - there seems to be a conflict with cairo-dock/openGL. smplayer has this same conflict but I get around it in all other files by wrapping smplayer with this command:
```
export XLIB_SKIP_ARGB_VISUALS=1
```

However, while this works fine for AVI and mpeg files it doesn't seem to work with MP4 files (or files encoded with 3GPP.

```

/usr/bin/mplayer -noquiet -nofs -nomouseinput -sub-fuzziness 1 -identify -slave -vo xv, -ao alsa -nokeepaspect -framedrop -nodr -double -input nodefault-bindings:conf=/dev/null -stop-xscreensaver -wid 73400666 -monitorpixelaspect 1 -*** -embeddedfonts -***-line-spacing 0 -***-font-scale 1 -***-styles /home/richard/.config/smplayer/styles.*** -fontconfig -font Arial -subfont-autoscale 0 -subfont-osd-scale 20 -subfont-text-scale 20 -subcp UTF-8 -vid 0 -aid 0 -subpos 100 -volume 100 -cache 2000 -osdlevel 0 -vf-add screenshot -slices -channels 2 -af scaletempo,equalizer=0:0:0:0:0:0:0:0:0:0 /home/richard/Pictures/Kids/StephensDay2010/video-2010-12-26-13-42-18.mp4

MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/richard/Pictures/Kids/StephensDay2010/video-2010-12-26-13-42-18.mp4.

Cache fill:  0.00% (0 bytes)   
libavformat file format detected.
ID_AUDIO_ID=0
ID_AID_0_LANG=eng
[lavf] stream 0: audio (aac), -aid 0, -alang eng
ID_VIDEO_ID=0
[lavf] stream 1: video (h264), -vid 0
Clip info:
 major_brand: 3gp4
ID_CLIP_INFO_NAME0=major_brand
ID_CLIP_INFO_VALUE0=3gp4
 minor_version: 768
ID_CLIP_INFO_NAME1=minor_version
ID_CLIP_INFO_VALUE1=768
 compatible_brands: 3gp43gp6
ID_CLIP_INFO_NAME2=compatible_brands
ID_CLIP_INFO_VALUE2=3gp43gp6
ID_CLIP_INFO_N=3
ID_FILENAME=/home/richard/Pictures/Kids/StephensDay2010/video-2010-12-26-13-42-18.mp4
ID_DEMUXER=lavfpref
ID_AUDIO_FORMAT=MP4A
ID_AUDIO_BITRATE=59728
ID_AUDIO_RATE=16000
ID_AUDIO_NCH=1
ID_START_TIME=0.00
ID_LENGTH=24.38
ID_SEEKABLE=1
ID_CHAPTERS=0
==========================================================================
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
AUDIO: 32000 Hz, 2 ch, s16le, 59.7 kbit/5.83% (ratio: 7466->128000)
ID_AUDIO_BITRATE=59728
ID_AUDIO_RATE=32000
ID_AUDIO_NCH=2
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
[equalizer] Limiting the number of filters to 9 due to low sample rate.
[equalizer] Limiting the number of filters to 9 due to low sample rate.
[equalizer] Limiting the number of filters to 9 due to low sample rate.
AO: [alsa] 48000Hz 2ch floatle (4 bytes per sample)
[equalizer] Limiting the number of filters to 9 due to low sample rate.
ID_AUDIO_CODEC=faad
Video: no video
Starting playback...
[A
[KSubtitles on
[A
[K

```

---

### Post by size_XXM on 2010-12-28
Try playing it with commandline mplayer and add '-vid 0' to the command. See if it plays.

---

### Post by andrew.46 on 2010-12-29
Hi size,

> **size_XXM said:**
> Try playing it with commandline mplayer and add '-vid 0' to the command. See if it plays.

Indeed, because the video stream is being missed:

```
ID_VIDEO_ID=0
[lavf] stream 1: video (h264), -vid 0

```

This problem has been encountered before and is an issue with the lavf demuxer, a solution is to use the mov demuxer instead. Some discussion and [solutions here]("http://smplayer.berlios.de/forum/viewtopic.php?f=2&t=375&start=0&sid=9818c691e096d3b6f1832cc4464ab412").

Andrew

---

### Post by pickarooney on 2010-12-29
> **size_XXM said:**
> Try playing it with commandline mplayer and add '-vid 0' to the command. See if it plays.

Should I try this even though it works from teh CLI without the switch, just to confirm that this is the problem?

I'll try with the mov demuxer once I've read through that thread.

Thanks

---

### Post by size_XXM on 2010-12-29
This is [known bug](https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/675179) in lavf demuxer which I ran into some time ago.
It was already fixed upstream but oh well... You can either have smplayer instruct mplayer not to use lavf, or do what I did - get a more recent mplayer from ripps: [https://launchpad.net/~ripps818/+archive/coreavc](https://launchpad.net/~ripps818/+archive/coreavc)

---

### Post by pickarooney on 2010-12-29
I'm really confused. mplayer does play this fine, but smplayer doesn't. I tried editing the mplayer config with extensions as in the link above but it doesn't do anything. 

Running mplayer from the command line with '-vid 0' I get no video output, just audio. 
So do I need to force smplayer to use -vid 1 somehow?

The mplayer version I have is 1.0rc4-4.4.5. I just added that PPA and upgraded but it makes no difference.

---

### Post by andrew.46 on 2010-12-29
Hi pickarooney,

> **pickarooney said:**
> I'm really confused. mplayer does play this fine, but smplayer doesn't. I tried editing the mplayer config with extensions as in the link above but it doesn't do anything.

After making the appropriate change to the mplayer config perhaps also try rvm's suggestion:

> 
(After this you need to play the video in smplayer at least once with the option "remember settings for all files" disabled, to force smplayer to forget the video id).[QUOTE]
[/QUOTE]

Andrew

---

### Post by pickarooney on 2010-12-29
Ah, I had missed that. It works! Thanks :)

---

### Post by andrew.46 on 2010-12-29
Hi pickarooney,

> **pickarooney said:**
> Ah, I had missed that. It works! Thanks :)

Excellent news :),

Andrew

---

