---
title: "gstreamer0.10-plugins-base won't upgrade :("
date: 2007-03-21
forum: Multimedia &amp; Video
---

### Post by GringoFrenzy on 2007-03-21
Hi guys and gals :D

When I first installed Ubuntu (6.06 LTS) at the weekend, I couldn't get any MP3s to play AT ALL through RhythmBox.  The app would just skip over them infinitely in my playlist, but would happily play .ogg files.

Anyway, being a n00b I thought maybe if I installed a different player I'd have more luck, so I installed Banshee through Synaptic (from a 3rd party repository), which upgraded all of my GStreamer plugins to version 0.10 as dependencies.

All except gstreamer0.10-plugins-base!

Basically, it's there in Synaptic, and it's marked for upgrade (with the little star), but everytime I try and force the upgrade it just leaves it alone, and doesn't actually give me any rationale for doing so.  I just CANNOT fathom what is causing this to happen.
I've even tried running 'sudo -i apt-get upgrade' from the Terminal FailSafe session at the GDM login screen, just in-case something on my gnome desktop was using the plugin or something, but I've had no luck.

How important is this plugin to playback of MP3s?  It sounds pretty essential from the description in Synaptic.

I've managed to get MP3 playback to work by installing the Fluendo plugin, but on a few songs I get a deep, bassy thud in the background, which definately isn't part of the song.  I think that might be related to the CBR/VBR issues other people are having.

I'm a complete Linux newbie (like I said, I only installed Ubuntu at the weekend), so forgive me if I've overlooked something basic.

I really did trawl through a load of forums before posting about this, and couldn't find anything similar to my issue.

Any advice is greatly appreciated, cheers!  :D

---

