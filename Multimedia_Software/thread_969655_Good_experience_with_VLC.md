---
title: "Good experience with VLC"
date: 2008-11-03
forum: Multimedia Software
---

### Post by arkmundi on 2008-11-03
Some of us just must have [http://www.pbs.org/wgbh/nova/](http://www.pbs.org/wgbh/nova/) programs available to us with a few clicks of the browser.  If you're like me, you encountered the difficulty that PBS NOVA only provide quicktime or windows media player streams.  And, desperate for a solution read lots of posts on this and other forums with various suggestions.  You even tried the "Comprehensive Multimedia & Video Howto" sticky guide.  And spent untold hours trying and trying again, with various suggestions.  Here's my set of brief suggestions:

1> DO NOT USE MPlayer or Medibuntu
2> Use VLC Media player instead
3> You'll need both the VLC Media Player and the mozilla-plugin-vlc {VLC will install from Applications Add/Remove; the plugin must, for now, be installed from the Synaptic Package Manager}
4> Deinstall the Totem Mozilla plugin {totem-mozilla}
5> after doing this, check by type "about:plugins" in your firefox browser address bar and insuring that the VLS Multimedia Plugin is there and enabled
6> I had to tweak a bit to get VCL to play both sound & video on my Dell Inspiron 1525n Ubuntu 8.04 system using ALSA sound; if you experience problems, please persist.

Thought I share this - I can now watch NOVA programs - what a relief!

---

### Post by arkmundi on 2008-11-04
Its worth noting that complete instructions for install VLC on Ubuntu can be found at:
  [http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

The sound strategy that worked for me is ALSA using Pulse, so the packages needed for that are:  vlc-plugin-esd, vlc-plugin-pulse.

If playing DVD's, package libdvdcss2.

Also of note:  
[http://en.wikipedia.org/wiki/VLC_media_player](http://en.wikipedia.org/wiki/VLC_media_player)
- VLC supports all codecs and all file formats supported by FFmpeg. This means that DVD Video and MPEG-4 playback as well as support for Ogg and Matroska (MKV) file formats work "out of the box". However, this feature is not unique to VLC, as any player using the FFmpeg libraries, including MPlayer and xine-lib-based players, can play those formats without need for external codecs. VLC also supports codecs that are not included in FFmpeg.

---

