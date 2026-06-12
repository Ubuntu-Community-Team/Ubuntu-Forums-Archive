---
title: "Keep losing my multimedia - it wont stick"
date: 2009-05-07
forum: Multimedia Software
---

### Post by dazzlindonna on 2009-05-07
Ever since I upgraded to Jaunty, I've had this problem where Flash, video, youtube, etc. works fine for a while, and then poof, it disappears.  I've finally gotten it down to where I have a script ready to run so that at any point during the day (and this happens nearly daily), I can easily restore everything.  But I can't for the life of me figure out why it goes away to begin with.

Generally, at least once a day, I have to run this:

```

sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse ia32-libs icedtea6-plugin libmp3lame0 non-free-codecs openjdk-6-jre unrar



sudo apt-get remove kaffeine-mozilla mozilla-helix-player mozilla-mplayer mozilla-plugin-vlc totem-mozilla xine-plugin



sudo apt-get install gnome-mplayer gecko-mediaplayer

```

Once I do that, I'm good to go for a while.  But a few hours later, or a day or so later, I'll realize that once again, I'm no longer able to see youtube videos or various other flash related goodies.  So, I run the code above again, and all is well again...until it's not again.

Am I the only one with this problem of the "daily disappearing multimedia"?  Any thoughts on why this would happen?

---

