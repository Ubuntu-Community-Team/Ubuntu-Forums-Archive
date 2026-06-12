---
title: "gecko-mediaplayer 1.0.4 doesn't play m4v on 12.04"
date: 2012-06-04
forum: Multimedia Software
---

### Post by nhtrader on 2012-06-04
mythbuntu 12.04 (64bit)
mythtv 0.25+fixes

Personal Home Web Server Check:
mythweb/apache2 server file: /etc/mime.types contains: video/x-m4v   m4v

Web Browser Info:
opera 11.64 plugins:gecko-mediaplayer 1.0.4
Opera MIME Type: video/x-m4v      m4v  || use plugin:gecko-mediaplayer 1.0.4 (exists)
Opera MIME Type: video/mp4      mp4  || use plugin:gecko-mediaplayer 1.0.4 (exists)

Chromium	18.0.1025.151 (Developer Build 130497) Ubuntu 12.04
OS	Linux
WebKit	535.19 (trunk@106313)
JavaScript	V8 3.8.9.16
Flash	11.2 r202
User Agent	Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/535.19 (KHTML, like Gecko) Ubuntu/12.04 Chromium/18.0.1025.151 Chrome/18.0.1025.151 Safari/535.19
Command Line	 /usr/lib/chromium-browser/chromium-browser --flag-switches-begin --flag-switches-end

mplayerplug-in is now gecko-mediaplayer 1.0.4
/usr/lib/mozilla/plugins/gecko-mediaplayer.so
Chrome MIME Type: video/x-m4v      m4v  (exists)
Chrome MIME Type: video/mp4      mp4  (exists)

QuickTime Plug-in 7.6.9
/usr/lib/mozilla/plugins/gecko-mediaplayer-qt.so
Chrome MIME Type: video/quicktime      mp4  (exists)

---------------------------------------------------------


I'm using either opera or chromium to access mythweb and have only gecko-mediaplayer plugin installed. I am trying to view an m4v video file, but it doesn't play.

Opera's response to m4v is to start gnome-mplayer, but nothing happens. No video; just controls appear. Tried to click icons "Play" then "Stop", "Play"; but still no movie.


Chromium doesn't play it either.
Chromium's response is to show a black field with an inactive play icon in the center. Moving the mouse over the icon doesn't change the cursor pointer to a "hand". No event is associated with the "play" icon.



What can I do to get gecko-player plugin to work? 
Why doesn't the Quicktime portion of the plugin "kick in"? 
Alternatively, why doesn't the plugin hand off the m4v file to mplayer so that it can play the file?


NOTE: I verified that the file works/plays by using these programs directly:
1. the m4v file plays fine in gnome player directly.
2. the same m4v file plays fine using CLI:  mplayer movie.m4v
3. VLC also plays the m4v file. 

VLC provides the following media information:
Stream 0
Type: Video
Codec: H264 - MPEG-4 AVC (part10)(avc1)
Resolution: 720x480
Framerate: 23.974758
Decoded Format: Planar 4:2:0 YUV
Stream 1
Type Audio
Codec MPEG AAC Audio (mp4a)
Language English
Channels Stereo
Sample Rate 48000 Hz
Stream 2
Type Audio
Codec A52 Audio (aka AC3)(a52)
Language English
Description Surround
Channels Stereo
Sample Rate 48000 Hz
Bitrate 448 kb/s

---

