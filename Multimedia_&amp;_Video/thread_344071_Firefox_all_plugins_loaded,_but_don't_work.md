---
title: "Firefox: all plugins loaded, but don't work"
date: 2007-01-22
forum: Multimedia &amp; Video
---

### Post by pickarooney on 2007-01-22
I've installed Firefox (32-bit Kubuntu) and all the media plugins recommended in the Wiki HOWTO, and when I type about: plugins the following are listed:

VLC Multimedia plugin
Helix DNA Plugin: RealPlayer G2 Plug-In Compatible
Java(TM) Plug-in 1.5.0_08-b03
Adobe Reader 7.0
Shockwave Flash
QuickTime Plug-in 6.0 / 7
RealPlayer 9
Windows Media Player Plugin
mplayerplug-in 3.31

When I go to [Quicktime](http://www.apple.com/trailers/) and click on a video, all that displays is (no video)
When I try to play Real Player content I get some picture but the sound is all chopped and there are green screens every half second. The version of realplayer installed on my system is 10 but shows as 9 in the plugins list.

I set the MMS protocol handler as described [here](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_handle_mss_protocol_in_Mozilla_Firefox) (except my vlc is in /usr/bin/vlc so I used that path) and RTSP handling as described [here](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_handle_rtsp_.28realmedia.29_protocol_in_Mozilla_Firefox)
but again with the corrected path to realplay.

In the Preferences section of Firefox, Content, File Types AVI/WMV files are associated with the Windows Media Player plugin and I can't choose another plugin such as the mplayer one. Likewise QT files are associated with the QuickTime plugin.

On another note, none of these plugins load when I run Swiftfox, but that's less important.

---

### Post by pickarooney on 2007-01-22
double post

---

