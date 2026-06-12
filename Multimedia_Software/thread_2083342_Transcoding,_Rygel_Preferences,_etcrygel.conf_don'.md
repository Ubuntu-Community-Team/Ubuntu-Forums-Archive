---
title: "Transcoding, Rygel Preferences, /etc/rygel.conf don't jive"
date: 2012-11-12
forum: Multimedia Software
---

### Post by cshep70 on 2012-11-12
12.04
Rygel installed through Synaptic

When I run 'rygel' from terminal everything appears to run as planned.  It harvests the /Music, /Videos and /Pictures forders and I can play them on my Android devices (Using MX Player for the odd video formats).  However, my Sony Media Player is very particular as to the types of video encoding it likes and chokes on most of the files I try to play.

I then edit /etc/rygel.conf to modify the lines for AAC_ISO_320, AVC_MP4, and GstLaunch all to 'true'.

When I run 'rygel' from terminal, nothing changes.  It harvests the folders and I get the message: 'GstLaunch' disabled by user, ignoring...  and I can play the files with client encoding only (no transcoding - so, not on the Sony).

When I run 'rygel -c /etc/rygel.conf it harvests the folders but I get the message:  New plugin 'GstLaunch' available.  From my Android, two Media Servers now show up:  'Gst Launch' and 'My Media'.  Both from Rygel.  The Gst Launch only has 2 built in files: Videotestsrc and Videotestscr with timeoverlay2.  The My Media server has all of my files that again must be played with client side encoding, no transcoding.

Things that confuse me:
1.  Rygel Preferences seems to make no changes to /etc/rygel.conf.
2.  Running unswitched 'rygel' from terminal does not seem to call /etc/rygel.conf

A question I'd like to learn an answer to:
1.  How can I get the rygel Media Server to transcode audio/video to an dlna compliant format so I can share them to my Sony Media Player?

Thanks for reading this entire thing,
Shep

---

### Post by aatz on 2012-11-12
I am having this exact same problem! Rygel preferences doesn't appear to do anything, and if it does rygel doesn't care. I thought it may have to do with the tracker which it automatically uses if it's installed but I uninstalled and used mediaexport plugin, same thing. I was really looking for a way to decide which folders for it to share, but would also like it to transcode things for my phone. I have seen pictures of a different rygel-preferences with many more options, maybe a previous version? Other than being un-configurable it works works well for me, to watch videos on a TV that will only connect to an x-box

---

### Post by micool121 on 2012-11-18
local rygel conf file is in
[user]/.config/rygel.conf


the one you'are modifing is root's one.

regards,

---

### Post by jensgeorg on 2012-11-22
> **cshep70 said:**
> 12.04
Rygel installed through Synaptic

When I run 'rygel' from terminal everything appears to run as planned.  It harvests the /Music, /Videos and /Pictures forders and I can play them on my Android devices (Using MX Player for the odd video formats).  However, my Sony Media Player is very particular as to the types of video encoding it likes and chokes on most of the files I try to play.

I then edit /etc/rygel.conf to modify the lines for AAC_ISO_320, AVC_MP4, and GstLaunch all to 'true'.


Those two are horribly broken in 0.14 (the version on 12.04). And, as others already said, the configuration to modify is ~/.config/rygel.conf

> 
When I run 'rygel' from terminal, nothing changes.  It harvests the folders and I get the message: 'GstLaunch' disabled by user, ignoring...  and I can play the files with client encoding only (no transcoding - so, not on the Sony).

When I run 'rygel -c /etc/rygel.conf it harvests the folders but I get the message:  New plugin 'GstLaunch' available.  From my Android, two Media Servers now show up:  'Gst Launch' and 'My Media'.  Both from Rygel.  The Gst Launch only has 2 built in files: Videotestsrc and Videotestscr with timeoverlay2.  The My Media server has all of my files that again must be played with client side encoding, no transcoding.


How do you know that there's no transcoding?

> 
Things that confuse me:
1.  Rygel Preferences seems to make no changes to /etc/rygel.conf.
2.  Running unswitched 'rygel' from terminal does not seem to call /etc/rygel.conf

A question I'd like to learn an answer to:
1.  How can I get the rygel Media Server to transcode audio/video to an dlna compliant format so I can share them to my Sony Media Player?

Thanks for reading this entire thing,
Shep

What kind of Sony device? For TV, BD Player and PS3 it should work out-of-the box if you have gst-ffmpeg installed, unless you have a north-american model.

---

### Post by jensgeorg on 2012-11-22
> **aatz said:**
> I am having this exact same problem! Rygel preferences doesn't appear to do anything, and if it does rygel doesn't care. I thought it may have to do with the tracker which it automatically uses if it's installed but I uninstalled and used mediaexport plugin, same thing. I was really looking for a way to decide which folders for it to share, but would also like it to transcode things for my phone. I have seen pictures of a different rygel-preferences with many more options, maybe a previous version? Other than being un-configurable it works works well for me, to watch videos on a TV that will only connect to an x-box

Sorry, the preferences tool is kind of a mess currently. It applies to MediaExport only.

Transcoding to your phone might work with 0.16.3 where the DLNA AVC profile is supported.

---

