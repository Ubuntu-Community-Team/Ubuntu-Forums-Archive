---
title: "[SOLVED] SMPLAYER Won't Play MP3"
date: 2008-04-19
forum: Multimedia &amp; Video
---

### Post by drs305 on 2008-04-19
I just downloaded smplayer and can't get it to play mp3s. If I open via the menu and select an mp3 file, it doesn't do anything. If I use mplayer or the 'open with' option of nautilus, mplayer works but smplayer just sits on the desktop and doesn't do anything. It doesn't even seem to try to open the file.

codecs, etc installed, and as I mentioned, mplayer works fine. I thought smplayer was just a front end for mplayer, so I don't understand why the latter works but the former doesn't. :-k

Added: I guess as long as I'm posting this, I might as well make this my annual request for a media player which can do what windows media player can do: play an internet stream at variable speeds without affecting pitch and allow me to advance the slider forward or backward in the broadcast without crashing or hanging up.

---

### Post by disturbedite on 2008-04-19
the first thing i would have done is the first thing you should have done:
Options --> View logs --> Mplayer.
post what is says when you try to play an mp3.

---

### Post by drs305 on 2008-04-19
Here is the output for smplayer when I try to play an mp3. There is apparently a problem with 'scaletempo', whatever that is telling me. I checked synaptic and libmad0 is installed, if that means anything...
```

Translator::loadCatalog: can't load qt_en_US from /usr/share/smplayer/translations
Translator::loadCatalog: can't load qt_en_US from /usr/share/qt4/translations
Translator::loadCatalog: successfully loaded smplayer_en_US from /usr/share/smplayer/translations
This is SMPlayer v. 0.5.62 (svn r418) running on Linux
Qt v. 4.3.2
 * application path: '/usr/bin'
 * data path: '/usr/share/smplayer'
 * translation path: '/usr/share/smplayer/translations'
 * doc path: '/usr/share/doc/packages/smplayer'
 * themes path: '/usr/share/smplayer/themes'
 * shortcuts path: '/usr/share/smplayer/shortcuts'
 * smplayer home path: '/home/drs64/.smplayer'
 * ini path: '/home/drs64/.smplayer'
main: files_to_play: count: 0
Recents::load
Core::Core: file_settings: '/home/drs64/.smplayer/smplayer_files.ini'
MplayerProcess::init_rx
MplayerLayer::allowClearingBackground: 0
Preferences::monitor_aspect_double
 warning: monitor_aspect couldn't be parsed!
 monitor_aspect set to 0
Playlist::setModified: 0
Playlist::loadSettings
Playlist::addItem: '/media/av/audio/music/test.mp3'
Playlist::setModified: 0
name: 'test.mp3'
Style name: 'plastique'
Style class name: 'QPlastiqueStyle'
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
DefaultGui::createControlWidgetMini
BaseGui::initializeMenus
BaseGui::updateRecents
DefaultGui::updateWidgets
BaseGui::updateWidgets
DefaultGui::loadConfig
DefaultGui::updateWidgets
BaseGui::updateWidgets
BaseGui::showEvent
BaseGui::loadActions
ActionsEditor::loadFromConfig
BaseGui::initializeMenus
BaseGui::updateRecents
DefaultGui::updateWidgets
BaseGui::updateWidgets
BaseGui::fileOpen
BaseGui::openFile: '/media/av/audio/music/test.mp3'
Core::openFile: '/media/av/audio/music/test.mp3'
Core::playNewFile: '/media/av/audio/music/test.mp3'
Core::saveMediaInfo
Core::checkHaveSettingsSaved: group_name: '_media_av_audio_music_test_mp3_6747980'
We have settings for this file!!!
Core::loadMediaInfo: '_media_av_audio_music_test_mp3_6747980'
MediaSettings::load
Media settings read
Core::playNewFile: volume: 40, old_volume: 40
Core::initPlaying
Core::startMplayer
Helper::setScreensaverEnabled: 0
Core::startMplayer: setting working directory to '/home/drs64/.smplayer/screenshots'
DesktopInfo::desktop_size: primary screen: 0
DesktopInfo::desktop_size: size of primary screen: 1280 x 1024
DesktopInfo::desktop_size: size of screen: 1280 x 1024
Core::startMplayer: command: '/usr/bin/mplayer -noquiet -nofs -afm hwac3 -sub-fuzziness 1 -identify -slave -ao alsa -zoom -nokeepaspect -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 35651598 -colorkey 131586 -monitoraspect 1.25 -subfont-autoscale 1 -subfont-text-scale 5 -subcp ISO-8859-1 -subpos 100 -contrast 0 -brightness 0 -hue 0 -saturation 0 -osdlevel 0 -vf-add expand=osd=1 -noslices -vf-add screenshot -channels 2 -af scaletempo -softvol -softvol-max 110 /media/av/audio/music/test.mp3'
MplayerLayer::playingStarted
BaseGui::calculateDiff: diff_size: 0, 0
BaseGui::calculateDiff: diff_size set to: 0, 129
MplayerProcess::init_rx
Core::tellmp: 'volume 40 1'
Playlist::setModified: 0
Playlist::addFiles
Playlist::addItem: '/media/av/audio/music/test.mp3'
name: 'test.mp3'
 * latest_dir: ''
MplayerProcess::parseLine: 'MPlayer 1.0rc2-4.1.3 (C) 2000-2007 MPlayer Team'
MplayerProcess::parseLine: MPlayer version found: 1.0rc2
MplayerProcess::parseLine: MPlayer SVN: 24722
MplayerProcess::parseLine: 'CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ (Family: 15, Model: 75, Stepping: 2)'
MplayerProcess::parseLine: 'CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1'
MplayerProcess::parseLine: 'Compiled with runtime CPU detection.'
MplayerProcess::parseLine: 'mplayer: could not connect to socket'
MplayerProcess::parseLine: 'mplayer: No such file or directory'
MplayerProcess::parseLine: 'Failed to open LIRC support. You will not be able to use your remote control.'
MplayerProcess::parseLine: 'Terminal type `unknown' is not defined.'
MplayerProcess::parseLine: ''
MplayerProcess::parseLine: 'Playing /media/av/audio/music/test.mp3.'
MplayerProcess::parseLine: 'ID_AUDIO_ID=0'
MplayerProcess::parseLine: ID_AUDIO_ID: 0
MplayerProcess::parseLine: 'Audio file file format detected.'
MplayerProcess::parseLine: 'Clip info:'
MplayerProcess::parseLine: ' Title: 5th Symphony'
MplayerProcess::parseLine: clip_name: '5th Symphony'
MplayerProcess::parseLine: 'ID_CLIP_INFO_NAME0=Title'
MplayerProcess::parseLine: 'ID_CLIP_INFO_VALUE0=5th Symphony'
MplayerProcess::parseLine: ' Artist: Beethoven '
MplayerProcess::parseLine: clip_artist: 'Beethoven '
MplayerProcess::parseLine: 'ID_CLIP_INFO_NAME1=Artist'
MplayerProcess::parseLine: 'ID_CLIP_INFO_VALUE1=Beethoven '
MplayerProcess::parseLine: ' Album: Classical'
MplayerProcess::parseLine: clip_album: 'Classical'
MplayerProcess::parseLine: 'ID_CLIP_INFO_NAME2=Album'
MplayerProcess::parseLine: 'ID_CLIP_INFO_VALUE2=Classical'
MplayerProcess::parseLine: ' Year: '
MplayerProcess::parseLine: clip_date: ''
MplayerProcess::parseLine: 'ID_CLIP_INFO_NAME3=Year'
MplayerProcess::parseLine: 'ID_CLIP_INFO_VALUE3='
MplayerProcess::parseLine: ' Comment: '
MplayerProcess::parseLine: clip_comment: ''
MplayerProcess::parseLine: 'ID_CLIP_INFO_NAME4=Comment'
MplayerProcess::parseLine: 'ID_CLIP_INFO_VALUE4='
MplayerProcess::parseLine: ' Genre: Classical'
MplayerProcess::parseLine: clip_genre: 'Classical'
MplayerProcess::parseLine: 'ID_CLIP_INFO_NAME5=Genre'
MplayerProcess::parseLine: 'ID_CLIP_INFO_VALUE5=Classical'
MplayerProcess::parseLine: 'ID_CLIP_INFO_N=6'
MplayerProcess::parseLine: 'ID_FILENAME=/media/av/audio/music/test.mp3'
MplayerProcess::parseLine: 'ID_DEMUXER=audio'
MplayerProcess::parseLine: 'ID_AUDIO_FORMAT=85'
MplayerProcess::parseLine: 'ID_AUDIO_BITRATE=128000'
MplayerProcess::parseLine: 'ID_AUDIO_RATE=44100'
MplayerProcess::parseLine: 'ID_AUDIO_NCH=0'
MplayerProcess::parseLine: 'ID_LENGTH=421.00'
MplayerProcess::parseLine: md.duration set to 421.000000
MplayerProcess::parseLine: '=========================================================================='
MplayerProcess::parseLine: 'Forced audio codec: mad'
MplayerProcess::parseLine: 'Opening audio decoder: [libmad] libmad mpeg audio decoder'
MplayerProcess::parseLine: 'AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)'
MplayerProcess::parseLine: 'ID_AUDIO_BITRATE=128000'
MplayerProcess::parseLine: 'ID_AUDIO_RATE=44100'
MplayerProcess::parseLine: 'ID_AUDIO_NCH=2'
MplayerProcess::parseLine: 'Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)'
MplayerProcess::parseLine: '=========================================================================='
MplayerProcess::parseLine: 'Couldn't find audio filter 'scaletempo''
MplayerProcess::parseLine: '[libaf] Couldn't create or open audio filter 'scaletempo''
MplayerProcess::parseLine: 'Error at audio filter chain pre-init!'
MplayerProcess::parseLine: ''
MplayerProcess::parseLine: 'Exiting... (Fatal error)'
MyProcess::procFinished
MyProcess::procFinished: Bytes available: 0
MplayerProcess::processFinished
Core::processFinished
Helper::setScreensaverEnabled: 1
Core::processFinished: we_are_restarting: 0
Core::processFinished: play has finished!
 exit_status: 0
MplayerLayer::playingStopped
BaseGui::showLog

```

---

### Post by drs305 on 2008-04-19
I found this regarding the scaletempo error and smplayer is working now:

Go to Preferences->General->Audio and select No for the option "High speed playback without altering the pitch".
[http://ubuntuforums.org/showthread.php?t=472149&page=16](http://ubuntuforums.org/showthread.php?t=472149&page=16)   Post #44

---

