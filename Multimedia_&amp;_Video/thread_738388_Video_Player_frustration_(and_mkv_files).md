---
title: "Video Player frustration (and mkv files)"
date: 2008-03-28
forum: Multimedia &amp; Video
---

### Post by Kiri on 2008-03-28
Hey I cannot get mkv files to playback properly in any video player.

In smplayer, there is no audio.
mplayer can play it ok with audio, but when I try to go full screen on the tv (secondary) screen, it doesnt size correctly and about 30% of the video is cut off to the right. Its very strange.
VLC player can playback, but I cant get full screen to work. When I go full screen on the tv screen it displays the full screen video on my laptop screen!  Plus it crashes sometimes. Frustrating!
Totem media player doesnt even play them at all.

Are there any stable video players that will work properly??
All the ones I've tried so far seem very buggy.

SMplayer has been the best, exceot fot he sound thing, and sometimes it will not display the video until I open once in full screen and then shrink it back down. 

Anyway, is there any ideas how I can get SMplayer to have audio with mkv files??
Or any better video players?

Its strange though, because I thought smplayer is just a front end for mplayer... but then why do I have audio in mplayer and none in smplayer?

Thanks for your help

---

### Post by rvm4000 on 2008-03-28
Try to change the audio driver in the preferences of smplayer. If that doesn't fix it, take a look at the mplayer log (options->view logs), maybe mplayer says why there's no audio.

For the problem with the video, try to enable or disable the option "Don't repaint the background of the video window" in preferences->advanced.

In the case you're using version 0.5.20 (which I think it's the one in Gutsy) I'd suggest to update: [http://smplayer.berlios.de/downloads.php](http://smplayer.berlios.de/downloads.php)

---

### Post by Kiri on 2008-03-29
Thanks for your reply. I couldn't find a place to change the audio driver in SMPlayer, but I tried toggling on and off several of the settings in the audio tab and for some reason it started working! I didn't actually change anything, but somehow messing about in there gave it a kick :)

Couldn't find "Don't repaint the background of the video window" option to play with... but the video issue is not so big for me, just a bit weird. I'm using version 0.6 RC.
Anyway, I can use it now, so its ok. 
Also tried out gxine which was quite good and played back well. So far those two are the best ones I found. I'll stick with SMPlayer for now. 

thanks again

---

### Post by rvm4000 on 2008-03-29
The audio driver can be changed in the General section (and first tab) in preferences. There are two comboboxes, one for the video and the other the audio.

"Don't repaint the background of the video window" is located in the Advanced section, near the end.

---

### Post by Kiri on 2008-03-29
Ok, this is weird. Now SMPlayer wont play mp4 files! 
No video, no sound, no nothing :(

I found the "Don't repaint the background of the video window", but it didnt help me unfortunately.

And the audio codec, I still cant see it. Can you see it in the screenshot I attached?

---

### Post by rvm4000 on 2008-03-29
> **Kiri said:**
> Ok, this is weird. Now SMPlayer wont play mp4 files! 
No video, no sound, no nothing :(

Take a look at the mplayer log (options->view logs) when that happens. 

> **Kiri said:**
> 
And the audio codec, I still cant see it. Can you see it in the screenshot I attached?

It's in the General tab, not in the audio tab.

[[IMG]http://img267.imageshack.us/img267/1164/smplayerau8.th.png[/IMG]](http://img267.imageshack.us/my.php?image=smplayerau8.png)

---

### Post by Kiri on 2008-03-29
Thanks! I see it now. Dunno how I missed it before... :oops:

And I'll check the log for clues next time too. 
It seems like SMPlayer is pretty temperamental for me, but I guess its not the final release yet. 
I'll see how it goes~

---

### Post by Kiri on 2008-03-30
SMPlayer stopped working again...  I cant see the video playing at all. No video, no audio. Just a blank screen

 I saved the logs. But I have no idea what they mean.

Here is the mplayer one:


```
/usr/bin/mplayer -noquiet -nofs -sub-fuzziness 1 -identify -msglevel demux=6 -slave -vo xv -ao pulse -zoom -nokeepaspect -framedrop -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 88080398 -colorkey 0x020202 -monitoraspect 1.6 -subfont-autoscale 2 -subfont-text-scale 4.2 -subcp ISO-8859-1 -aid 0 -subpos 100 -contrast 0 -brightness 0 -hue 0 -saturation 0 -nocache -osdlevel 0 -vf-add screenshot -channels 2 -softvol -softvol-max 110 /media/cdrom0/Samurai Champloo/(B-A)Samurai_Champloo_-_21_(820387E0).mkv

MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz (Family: 6, Model: 15, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
Terminal type `unknown' is not defined.

Playing /media/cdrom0/Samurai Champloo/(B-A)Samurai_Champloo_-_21_(820387E0).mkv.
Checking for YUV4MPEG2
Checking for NuppelVideo
Checking for REAL
Checking for SMJPEG
[mkv] Found the head...
[mkv] + a segment...
[mkv] /---- [ parsing seek head ] ---------
[mkv] /---- [ parsing seek head ] ---------
[mkv] \---- [ parsing seek head ] ---------
[mkv] /---- [ parsing cues ] -----------
[mkv] \---- [ parsing cues ] -----------
[mkv] \---- [ parsing seek head ] ---------
[mkv] |+ segment information...
[mkv] | + timecode scale: 1000000
[mkv] | + duration: 1401.318s
[mkv] |+ segment tracks...
[mkv] | + a track...
[mkv] |  + Track number: 1
[mkv] |  + Track type: Video
[mkv] |  + Default flag: 1
[mkv] |  + Codec ID: V_MS/VFW/FOURCC
[mkv] |  + CodecPrivate, length 40
[mkv] |  + Default duration: 41.708ms ( = 23.976 fps)
[mkv] |  + Language: und
[mkv] |  + Video track
[mkv] |   + Pixel width: 712
[mkv] |   + Pixel height: 480
[mkv] |   + Display width: 853
[mkv] |   + Display height: 480
[mkv] | + a track...
[mkv] |  + Track number: 2
[mkv] |  + Track type: Audio
[mkv] |  + Default flag: 1
[mkv] |  + Codec ID: A_AAC/MPEG4/LC/SBR
[mkv] |  + Default duration: 42.667ms ( = 23.438 fps)
[mkv] |  + Language: jpn
[mkv] |  + Audio track
[mkv] |   + Sampling frequency: 24000.000000
[mkv] |   + Channels: 6
[mkv] | + a track...
[mkv] |  + Track number: 3
[mkv] |  + Track type: Audio
[mkv] |  + Default flag: 0
[mkv] |  + Codec ID: A_AAC/MPEG4/LC/SBR
[mkv] |  + Default duration: 42.667ms ( = 23.438 fps)
[mkv] |  + Language: eng
[mkv] |  + Audio track
[mkv] |   + Sampling frequency: 24000.000000
[mkv] |   + Channels: 6
[mkv] | + a track...
[mkv] |  + Track number: 4
[mkv] |  + Track type: Subtitle
[mkv] |  + Default flag: 1
[mkv] |  + Codec ID: S_TEXT/UTF8
[mkv] |  + Language: eng
[mkv] |+ found cluster, headers are parsed completely :)
ID_VIDEO_ID=0
[mkv] Aspect: 1.777083
[mkv] Track ID 1: video (V_MS/VFW/FOURCC), -vid 0
ID_AUDIO_ID=0
ID_AID_0_LANG=jpn
[mkv] Track ID 2: audio (A_AAC/MPEG4/LC/SBR), -aid 0, -alang jpn
ID_AUDIO_ID=1
ID_AID_1_LANG=eng
[mkv] Track ID 3: audio (A_AAC/MPEG4/LC/SBR), -aid 1, -alang eng
ID_SUBTITLE_ID=0
ID_SID_0_LANG=eng
[mkv] Track ID 4: subtitles (S_TEXT/UTF8), -sid 0, -slang eng
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [XVID]  712x480  16bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
ID_FILENAME=/media/cdrom0/Samurai Champloo/(B-A)Samurai_Champloo_-_21_(820387E0).mkv
ID_DEMUXER=mkv
ID_VIDEO_FORMAT=XVID
ID_VIDEO_BITRATE=0
ID_VIDEO_WIDTH=712
ID_VIDEO_HEIGHT=480
ID_VIDEO_FPS=23.976
ID_VIDEO_ASPECT=1.7771
ID_AUDIO_FORMAT=MP4A
ID_AUDIO_BITRATE=0
ID_AUDIO_RATE=48000
ID_AUDIO_NCH=6
ID_LENGTH=1401.32
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
Opening video filter: [screenshot]
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
ID_VIDEO_CODEC=ffodivx
==========================================================================
Forced audio codec: mad
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
FAAD: compressed input bitrate missing, assuming 128kbit/s!
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
ID_AUDIO_BITRATE=128000
ID_AUDIO_RATE=48000
ID_AUDIO_NCH=2
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio) decoder)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
ID_AUDIO_CODEC=faad
Starting playback...
VDec: vo config request - 712 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
ID_VIDEO_ASPECT=1.7771
SwScaler: reducing / aligning filtersize 5 -> 4
SwScaler: reducing / aligning filtersize 5 -> 4
SwScaler: reducing / aligning filtersize 1 -> 1
SwScaler: reducing / aligning filtersize 5 -> 4
[swscaler @ 0x89348f0]SwScaler: BICUBIC scaler, from yuv420p to bgr24 using MMX2
[swscaler @ 0x89348f0]SwScaler: using 4-tap MMX scaler for horizontal luminance scaling
[swscaler @ 0x89348f0]SwScaler: using 4-tap MMX scaler for horizontal chrominance scaling
[swscaler @ 0x89348f0]SwScaler: using n-tap MMX scaler for vertical scaling (BGR)
[swscaler @ 0x89348f0]SwScaler: using MMX2 YV12->BGR24 Converter
[swscaler @ 0x89348f0]SwScaler: 712x480 -> 852x480
VO: [xv] 712x480 => 852x480 Planar YV12  [zoom]
X11 error: BadAccess during XSelectInput Call
X11 error: The 'ButtonPressMask' mask of specified window has probably already used by another appication (see man XSelectInput)
X11 error: MPlayer discards mouse control (reconfiguring)
```




Here is the SMPlayer one:


```
Translator::loadCatalog: can't load qt_en_US from /usr/share/smplayer/translations
Translator::loadCatalog: can't load qt_en_US from /usr/share/qt4/translations
Translator::loadCatalog: successfully loaded smplayer_en_US from /usr/share/smplayer/translations
This is SMPlayer v. 0.6.0rc2 (SVN 834) running on Linux
Qt v. 4.3.3
 * application path: '/usr/bin'
 * data path: '/usr/share/smplayer'
 * translation path: '/usr/share/smplayer/translations'
 * doc path: '/usr/share/doc/packages/smplayer'
 * themes path: '/usr/share/smplayer/themes'
 * shortcuts path: '/usr/share/smplayer/shortcuts'
 * smplayer home path: '/home/ki/.smplayer'
 * ini path: '/home/ki/.smplayer'
 * current path: '/home/ki'
main: files_to_play: count: 1
main: files_to_play[0]: '/media/cdrom0/Samurai Champloo/(B-A)Samurai_Champloo_-_21_(820387E0).mkv'
main: changed working directory to app path
main: current directory: /usr/bin
Recents::load
Core::Core: file_settings: '/home/ki/.smplayer/smplayer_files.ini'
MplayerProcess::init_rx
MplayerLayer::allowClearingBackground: 0
Preferences::monitor_aspect_double
 warning: monitor_aspect couldn't be parsed!
 monitor_aspect set to 0
Playlist::setModified: 0
Playlist::loadSettings
Playlist::addItem: '/media/cdrom0/Samurai Champloo/(B-A)Samurai_Champloo_-_21_(820387E0).mkv'
Playlist::setModified: 0
name: '(B-A)Samurai_Champloo_-_21_(820387E0).mkv'
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
BaseGui::showEvent
BaseGui::openFiles
Playlist::setModified: 0
Playlist::addFiles
Playlist::addItem: '/media/cdrom0/Samurai Champloo/(B-A)Samurai_Champloo_-_21_(820387E0).mkv'
name: '(B-A)Samurai_Champloo_-_21_(820387E0).mkv'
 * latest_dir: ''
BaseGui::open: '/media/cdrom0/Samurai Champloo/(B-A)Samurai_Champloo_-_21_(820387E0).mkv'
Core::open: '/media/cdrom0/Samurai Champloo/(B-A)Samurai_Champloo_-_21_(820387E0).mkv'
 * identified as local file
Core::openFile: '/media/cdrom0/Samurai Champloo/(B-A)Samurai_Champloo_-_21_(820387E0).mkv'
Core::playNewFile: '/media/cdrom0/Samurai Champloo/(B-A)Samurai_Champloo_-_21_(820387E0).mkv'
Core::saveMediaInfo
Core::checkHaveSettingsSaved: group_name: '_media_cdrom0_Samurai_Champloo_(B-A)Samurai_Champloo_-_21_(820387E0)_mkv_178909886'
We have settings for this file!!!
Core::loadMediaInfo: '_media_cdrom0_Samurai_Champloo_(B-A)Samurai_Champloo_-_21_(820387E0)_mkv_178909886'
MediaSettings::load
Media settings read
Core::playNewFile: volume: 100, old_volume: 40
Core::initPlaying
Core::startMplayer
Core::startMplayer: setting working directory to '/home/ki/.smplayer/screenshots'
DesktopInfo::desktop_size: primary screen: 0
DesktopInfo::desktop_size: size of primary screen: 2304 x 800
DesktopInfo::desktop_size: size of screen: 1280 x 800
MplayerVersion::isMplayerAtLeast: comparing 24924 with 24722
Core::startMplayer: command: '/usr/bin/mplayer -noquiet -nofs -sub-fuzziness 1 -identify -msglevel demux=6 -slave -vo xv -ao pulse -zoom -nokeepaspect -framedrop -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 88080398 -colorkey 0x020202 -monitoraspect 1.6 -subfont-autoscale 2 -subfont-text-scale 4.2 -subcp ISO-8859-1 -aid 0 -subpos 100 -contrast 0 -brightness 0 -hue 0 -saturation 0 -nocache -osdlevel 0 -vf-add screenshot -channels 2 -softvol -softvol-max 110 /media/cdrom0/Samurai Champloo/(B-A)Samurai_Champloo_-_21_(820387E0).mkv'
MplayerLayer::playingStarted
BaseGui::calculateDiff: diff_size: 0, 0
BaseGui::calculateDiff: diff_size set to: 0, 107
MplayerProcess::init_rx
BaseGui::loadActions
ActionsEditor::loadFromConfig
BaseGui::initializeMenus
BaseGui::updateRecents
DefaultGui::updateWidgets
BaseGui::updateWidgets
MplayerProcess::parseLine: 'MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team'
MplayerVersion::mplayerVersion: MPlayer version found: 1.0rc2
MplayerProcess::parseLine: MPlayer SVN: 24722
MplayerProcess::parseLine: 'CPU: Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz (Family: 6, Model: 15, Stepping: 6)'
MplayerProcess::parseLine: 'CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1'
MplayerProcess::parseLine: 'Compiled with runtime CPU detection.'
MplayerProcess::parseLine: 'mplayer: could not connect to socket'
MplayerProcess::parseLine: 'mplayer: No such file or directory'
MplayerProcess::parseLine: 'Failed to open LIRC support. You will not be able to use your remote control.'
MplayerProcess::parseLine: 'Terminal type `unknown' is not defined.'
MplayerProcess::parseLine: ''
MplayerProcess::parseLine: 'Playing /media/cdrom0/Samurai Champloo/(B-A)Samurai_Champloo_-_21_(820387E0).mkv.'
MplayerProcess::parseLine: 'Checking for YUV4MPEG2'
MplayerProcess::parseLine: 'Checking for NuppelVideo'
MplayerProcess::parseLine: 'Checking for REAL'
MplayerProcess::parseLine: 'Checking for SMJPEG'
MplayerProcess::parseLine: '[mkv] Found the head...'
MplayerProcess::parseLine: '[mkv] + a segment...'
MplayerProcess::parseLine: '[mkv] /---- [ parsing seek head ] ---------'
MplayerProcess::parseLine: '[mkv] /---- [ parsing seek head ] ---------'
MplayerProcess::parseLine: '[mkv] \---- [ parsing seek head ] ---------'
MplayerProcess::parseLine: '[mkv] /---- [ parsing cues ] -----------'
MplayerProcess::parseLine: '[mkv] \---- [ parsing cues ] -----------'
MplayerProcess::parseLine: '[mkv] \---- [ parsing seek head ] ---------'
MplayerProcess::parseLine: '[mkv] |+ segment information...'
MplayerProcess::parseLine: '[mkv] | + timecode scale: 1000000'
MplayerProcess::parseLine: '[mkv] | + duration: 1401.318s'
MplayerProcess::parseLine: '[mkv] |+ segment tracks...'
MplayerProcess::parseLine: '[mkv] | + a track...'
MplayerProcess::parseLine: '[mkv] |  + Track number: 1'
MplayerProcess::parseLine: '[mkv] |  + Track type: Video'
MplayerProcess::parseLine: '[mkv] |  + Default flag: 1'
MplayerProcess::parseLine: '[mkv] |  + Codec ID: V_MS/VFW/FOURCC'
MplayerProcess::parseLine: '[mkv] |  + CodecPrivate, length 40'
MplayerProcess::parseLine: '[mkv] |  + Default duration: 41.708ms ( = 23.976 fps)'
MplayerProcess::parseLine: '[mkv] |  + Language: und'
MplayerProcess::parseLine: '[mkv] |  + Video track'
MplayerProcess::parseLine: '[mkv] |   + Pixel width: 712'
MplayerProcess::parseLine: '[mkv] |   + Pixel height: 480'
MplayerProcess::parseLine: '[mkv] |   + Display width: 853'
MplayerProcess::parseLine: '[mkv] |   + Display height: 480'
MplayerProcess::parseLine: '[mkv] | + a track...'
MplayerProcess::parseLine: '[mkv] |  + Track number: 2'
MplayerProcess::parseLine: '[mkv] |  + Track type: Audio'
MplayerProcess::parseLine: '[mkv] |  + Default flag: 1'
MplayerProcess::parseLine: '[mkv] |  + Codec ID: A_AAC/MPEG4/LC/SBR'
MplayerProcess::parseLine: '[mkv] |  + Default duration: 42.667ms ( = 23.438 fps)'
MplayerProcess::parseLine: '[mkv] |  + Language: jpn'
MplayerProcess::parseLine: '[mkv] |  + Audio track'
MplayerProcess::parseLine: '[mkv] |   + Sampling frequency: 24000.000000'
MplayerProcess::parseLine: '[mkv] |   + Channels: 6'
MplayerProcess::parseLine: '[mkv] | + a track...'
MplayerProcess::parseLine: '[mkv] |  + Track number: 3'
MplayerProcess::parseLine: '[mkv] |  + Track type: Audio'
MplayerProcess::parseLine: '[mkv] |  + Default flag: 0'
MplayerProcess::parseLine: '[mkv] |  + Codec ID: A_AAC/MPEG4/LC/SBR'
MplayerProcess::parseLine: '[mkv] |  + Default duration: 42.667ms ( = 23.438 fps)'
MplayerProcess::parseLine: '[mkv] |  + Language: eng'
MplayerProcess::parseLine: '[mkv] |  + Audio track'
MplayerProcess::parseLine: '[mkv] |   + Sampling frequency: 24000.000000'
MplayerProcess::parseLine: '[mkv] |   + Channels: 6'
MplayerProcess::parseLine: '[mkv] | + a track...'
MplayerProcess::parseLine: '[mkv] |  + Track number: 4'
MplayerProcess::parseLine: '[mkv] |  + Track type: Subtitle'
MplayerProcess::parseLine: '[mkv] |  + Default flag: 1'
MplayerProcess::parseLine: '[mkv] |  + Codec ID: S_TEXT/UTF8'
MplayerProcess::parseLine: '[mkv] |  + Language: eng'
MplayerProcess::parseLine: '[mkv] |+ found cluster, headers are parsed completely :)'
MplayerProcess::parseLine: 'ID_VIDEO_ID=0'
MplayerProcess::parseLine: '[mkv] Aspect: 1.777083'
MplayerProcess::parseLine: '[mkv] Track ID 1: video (V_MS/VFW/FOURCC), -vid 0'
MplayerProcess::parseLine: 'ID_AUDIO_ID=0'
MplayerProcess::parseLine: ID_AUDIO_ID: 0
MplayerProcess::parseLine: 'ID_AID_0_LANG=jpn'
MplayerProcess::parseLine: Audio: ID: 0, Lang: 'jpn' Type: 'LANG'
MplayerProcess::parseLine: '[mkv] Track ID 2: audio (A_AAC/MPEG4/LC/SBR), -aid 0, -alang jpn'
MplayerProcess::parseLine: 'ID_AUDIO_ID=1'
MplayerProcess::parseLine: ID_AUDIO_ID: 1
MplayerProcess::parseLine: 'ID_AID_1_LANG=eng'
MplayerProcess::parseLine: Audio: ID: 1, Lang: 'eng' Type: 'LANG'
MplayerProcess::parseLine: '[mkv] Track ID 3: audio (A_AAC/MPEG4/LC/SBR), -aid 1, -alang eng'
MplayerProcess::parseLine: 'ID_SUBTITLE_ID=0'
SubTracks::process: 'ID_SUBTITLE_ID=0'
SubTracks::find: item type: 1, ID: 0 doesn't exist
MplayerProcess::parseLine: 'ID_SID_0_LANG=eng'
SubTracks::process: 'ID_SID_0_LANG=eng'
MplayerProcess::parseLine: '[mkv] Track ID 4: subtitles (S_TEXT/UTF8), -sid 0, -slang eng'
MplayerProcess::parseLine: '[mkv] Will play video track 1.'
MplayerProcess::parseLine: 'Matroska file format detected.'
MplayerProcess::parseLine: 'VIDEO:  [XVID]  712x480  16bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)'
MplayerProcess::parseLine: 'ID_FILENAME=/media/cdrom0/Samurai Champloo/(B-A)Samurai_Champloo_-_21_(820387E0).mkv'
MplayerProcess::parseLine: 'ID_DEMUXER=mkv'
MplayerProcess::parseLine: 'ID_VIDEO_FORMAT=XVID'
MplayerProcess::parseLine: 'ID_VIDEO_BITRATE=0'
MplayerProcess::parseLine: 'ID_VIDEO_WIDTH=712'
MplayerProcess::parseLine: md.video_width set to 712
MplayerProcess::parseLine: 'ID_VIDEO_HEIGHT=480'
MplayerProcess::parseLine: md.video_height set to 480
MplayerProcess::parseLine: 'ID_VIDEO_FPS=23.976'
MplayerProcess::parseLine: 'ID_VIDEO_ASPECT=1.7771'
MplayerProcess::parseLine: md.video_aspect set to 1.777100
MplayerProcess::parseLine: 'ID_AUDIO_FORMAT=MP4A'
MplayerProcess::parseLine: 'ID_AUDIO_BITRATE=0'
MplayerProcess::parseLine: 'ID_AUDIO_RATE=48000'
MplayerProcess::parseLine: 'ID_AUDIO_NCH=6'
MplayerProcess::parseLine: 'ID_LENGTH=1401.32'
MplayerProcess::parseLine: md.duration set to 1401.320000
MplayerProcess::parseLine: 'xscreensaver_disable: Could not find XScreenSaver window.'
MplayerProcess::parseLine: 'GNOME screensaver disabled'
MplayerProcess::parseLine: 'Opening video filter: [screenshot]'
MplayerProcess::parseLine: '=========================================================================='
MplayerProcess::parseLine: 'Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family'
MplayerProcess::parseLine: 'Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)'
MplayerProcess::parseLine: '=========================================================================='
MplayerProcess::parseLine: 'ID_VIDEO_CODEC=ffodivx'
MplayerProcess::parseLine: '=========================================================================='
MplayerProcess::parseLine: 'Forced audio codec: mad'
MplayerProcess::parseLine: 'Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)'
MplayerProcess::parseLine: 'FAAD: compressed input bitrate missing, assuming 128kbit/s!'
MplayerProcess::parseLine: 'AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)'
MplayerProcess::parseLine: 'ID_AUDIO_BITRATE=128000'
MplayerProcess::parseLine: 'ID_AUDIO_RATE=48000'
MplayerProcess::parseLine: 'ID_AUDIO_NCH=2'
MplayerProcess::parseLine: 'Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio) decoder)'
MplayerProcess::parseLine: '=========================================================================='
MplayerProcess::parseLine: 'AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)'
Core::gotAO: 'pulse'
MplayerProcess::parseLine: 'ID_AUDIO_CODEC=faad'
MplayerProcess::parseLine: 'Starting playback...'
MplayerProcess::parseLine: 'VDec: vo config request - 712 x 480 (preferred colorspace: Planar YV12)'
MplayerProcess::parseLine: 'VDec: using Planar YV12 as output csp (no 0)'
MplayerProcess::parseLine: 'Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.'
MplayerProcess::parseLine: md.video_aspect set to 1.780000
MplayerProcess::parseLine: 'ID_VIDEO_ASPECT=1.7771'
MplayerProcess::parseLine: md.video_aspect set to 1.777100
MplayerProcess::parseLine: 'SwScaler: reducing / aligning filtersize 5 -> 4'
MplayerProcess::parseLine: 'SwScaler: reducing / aligning filtersize 5 -> 4'
MplayerProcess::parseLine: 'SwScaler: reducing / aligning filtersize 1 -> 1'
MplayerProcess::parseLine: 'SwScaler: reducing / aligning filtersize 5 -> 4'
MplayerProcess::parseLine: '[swscaler @ 0x89348f0]SwScaler: BICUBIC scaler, from yuv420p to bgr24 using MMX2'
MplayerProcess::parseLine: '[swscaler @ 0x89348f0]SwScaler: using 4-tap MMX scaler for horizontal luminance scaling'
MplayerProcess::parseLine: '[swscaler @ 0x89348f0]SwScaler: using 4-tap MMX scaler for horizontal chrominance scaling'
MplayerProcess::parseLine: '[swscaler @ 0x89348f0]SwScaler: using n-tap MMX scaler for vertical scaling (BGR)'
MplayerProcess::parseLine: '[swscaler @ 0x89348f0]SwScaler: using MMX2 YV12->BGR24 Converter'
MplayerProcess::parseLine: '[swscaler @ 0x89348f0]SwScaler: 712x480 -> 852x480'
MplayerProcess::parseLine: 'VO: [xv] 712x480 => 852x480 Planar YV12  [zoom]'
Core::gotVO: 'xv'
Core::gotWindowResolution: 852, 480
BaseGuiPlus::resizeWindow: 852, 480
BaseGui::resizeWindow: 852, 480
BaseGui::resizeWindow: size to scale: 852, 480
BaseGui::resizeWindow: temp window size: 852, 587
BaseGui::resizeWindow: temp panel->size: 852, 456
BaseGui::resizeWindow: diff: 0, 131
BaseGui::resizeWindow: done: window size: 852, 611
BaseGui::resizeWindow: done: panel->size: 852, 480
BaseGui::resizeWindow: done: mplayerwindow->size: 852, 480
MplayerProcess::parseLine: 'X11 error: BadAccess during XSelectInput Call'
MplayerProcess::parseLine: 'X11 error: The 'ButtonPressMask' mask of specified window has probably already used by another appication (see man XSelectInput)'
MplayerProcess::parseLine: 'X11 error: MPlayer discards mouse control (reconfiguring)'
MplayerProcess::parseLine: starting sec: 0.000000
Core::gotStartingTime: 0.000000
Core::gotStartingTime: current_sec: 0.000000
Core::finishRestart
Core::newMediaPlaying
Core::initializeMenus
BaseGui::initializeMenus
MediaData::list
  filename: '/media/cdrom0/Samurai Champloo/(B-A)Samurai_Champloo_-_21_(820387E0).mkv'
  duration: 1401.320000
  video_width: 712
  video_height: 480
  video_aspect: 1.777100
  type: 0
  novideo: 0
  dvd_id: ''
  initialized: 1
  mkv_chapters: 0
  Subs:
SubTracks::list: item 0: type: 1 ID: 0 lang: 'eng' name: '' filename: ''
  Audios:
    item # 0
     ID: '0' lang: 'jpn' name: ''
     filename: '' duration: 0.000000 chapters: 0 angles: 0
    item # 1
     ID: '1' lang: 'eng' name: ''
     filename: '' duration: 0.000000 chapters: 0 angles: 0
  Titles:
  demuxer: 'mkv'
  video_format: 'XVID'
  audio_format: 'MP4A'
  video_bitrate: 0
  video_fps: '23.976'
  audio_bitrate: 128000
  audio_rate: 48000
  audio_nch: 2
  video_codec: 'ffodivx'
  audio_codec: 'faad'
MediaSettings::list
  current_sec: 0.000000
  current_sub_id: 0
  current_audio_id: 0
  current_title_id: -1000
  current_chapter_id: 0
  current_angle_id: -1000
  aspect_ratio_id: 1
  volume: 100
  mute: 0
  external_subtitles: ''
  external_audio: ''
  sub_delay: 0
  audio_delay: 0
  sub_pos: 100
  sub_scale: 4.200000
  sub_scale_ass: 1.000000
  brightness: 0
  contrast: 0
  gamma: 0
  hue: 0
  saturation: 0
  speed: 1.000000
  phase_filter: 0
  current_denoiser: 0
  deblock_filter: 0
  dering_filter: 0
  noise_filter: 0
  postprocessing_filter: 0
  upscaling_filter: 0
  current_deinterlacer: 0
  add_letterbox: 0
  karaoke_filter: 0
  extrastereo_filter: 0
  volnorm_filter: 0
  audio_use_channels: 2
  stereo_mode: 0
  panscan_factor: 1.000000
  flip: 0
  forced_demuxer: ''
  forced_video_codec: ''
  forced_audio_codec: ''
  original_demuxer: ''
  original_video_codec: ''
  original_audio_codec: ''
  mplayer_additional_options: ''
  mplayer_additional_video_filters: ''
  mplayer_additional_audio_filters: ''
  win_width: 852
  win_height: 480
  win_aspect(): 1.775000
  starting_time: 0.000000
  is264andHD: 0
Core::changeSubtitle: 0
Core::changeSubtitle: ID: 0
MplayerVersion::isMplayerAtLeast: comparing 25158 with 24722
Core::tellmp: 'sub_select 0'
Core::updateWidgets
DefaultGui::updateWidgets
BaseGui::updateWidgets
Core::changeAspectRatio: 1
Core::changeAspectRatio: mset.win_width 852, mset.win_height: 480
Core::setGamma: 0
Core::tellmp: 'gamma 0 1'
Core::displayMessage
Core::changePanscan: 1.000000
Core::displayMessage
Core::autosaveMplayerLog
Core::checkIfVideoIsHD
DefaultGui::enableActionsOnPlaying
BaseGui::enableActionsOnPlaying
BaseGui::newMediaLoaded
Recents::add: '/media/cdrom0/Samurai Champloo/(B-A)Samurai_Champloo_-_21_(820387E0).mkv'
BaseGui::updateRecents
Playlist:: getMediaInfo
name: '(B-A)Samurai_Champloo_-_21_(820387E0).mkv'
BaseGuiPlus::updateMediaInfo
BaseGui::updateMediaInfo
Core::updateWidgets
DefaultGui::updateWidgets
BaseGui::updateWidgets
BaseGui::displayState: Playing
mplayer reports that now it's playing
BaseGui::showMplayerLog
BaseGui::showLog
```



What might be the problem here?

---

### Post by rvm4000 on 2008-03-30
I don't know. There isn't any error in the logs. The file seems to be playing ok, with video and sound.

Anyway I would change the audio driver from "pulse" to another thing (alsa, oss, esd...). I don't know what "pulse" is.

Also try to update smplayer to 0.6.0rc3: [http://smplayer.sourceforge.net/downloads.php](http://smplayer.sourceforge.net/downloads.php) (or better to the latest svn: [ftp://ftp.berlios.de/pub/smplayer/ubuntu/](ftp://ftp.berlios.de/pub/smplayer/ubuntu/))

---

