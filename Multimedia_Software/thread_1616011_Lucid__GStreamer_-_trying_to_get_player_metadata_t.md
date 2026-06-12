---
title: "Lucid / GStreamer - trying to get player metadata to shoutcast."
date: 2010-11-07
forum: Multimedia Software
---

### Post by features on 2010-11-07
Hi all,

At work, we use the following script to pipe the output of the soundcard to a shoutcast server on the same box
```
#! /bin/bash

# Sets up a simple gstreamer chain that hauls data off an alsa device 
# and spits it out to the streaming server
#

LANG=C GST_DEBUG=1 gst-launch -mv pulsesrc device=alsa_output.pci-0000_00_1f.5.analog-stereo.monitor ! queue ! audioconvert ! queue ! lame bitrate=160 ! queue ! shout2send sync=true password=blahblah mount=/stream port=8000 ip=localhost 
```

It's a bit clunky, but it suits our purposes (one playlist to rule them all).

This doesn't transfer the song metadata from the player though.  It's visible in Pulseaudio's volume control, so it must be accessible somehow, but I've not found a way to do it yet.  Anybody got any ideas?  It only needs to write it to a file, and shoutcast can do the rest.

---

