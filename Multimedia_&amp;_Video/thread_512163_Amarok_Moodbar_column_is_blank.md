---
title: "Amarok: Moodbar column is blank"
date: 2007-07-28
forum: Multimedia &amp; Video
---

### Post by phyzome on 2007-07-28
I just installed the new moodbar package, but Amarok (1.4.6) is giving me a blank Mood column.

[LIST=1]
[*]Enabled moodbar in the Amarok settings
[*]Turned on the mood column
[*]Noticed that the words "Queuing" and "Calculating" appear in the mood column, followed by nothing
[*]Verified that ```
moodbar -o test.mood something.ogg
``` produces a mood file
[*]Tried restarting Amarok, with same results
[/LIST]

----

Okay, as it turns out, moodbar is failing on MP3 files, and I tested it manually against an OGG file. So I know what to fix now.

---

### Post by r4e on 2008-03-08
The package moodbar depends upon gstreamer, which uses plugins to decode various different media types including mp3.

The Amarok wiki says that the mad plugin should be used over ffmpeg plugin:

[http://amarok.kde.org/wiki/Moodbar#Troubleshooting](http://amarok.kde.org/wiki/Moodbar#Troubleshooting)

From the looks of it in gstreamer 0.10.7, the mad plugin got assimilated into the the gstreamer ugly plugins package:

[http://gstreamer.freedesktop.org/data/doc/gstreamer/head/gst-plugins-ugly-plugins/html/gst-plugins-ugly-plugins-plugin-mad.html](http://gstreamer.freedesktop.org/data/doc/gstreamer/head/gst-plugins-ugly-plugins/html/gst-plugins-ugly-plugins-plugin-mad.html)

I installed all of the the gstreamer ugly packages:

gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-dbg
gstreamer0.10-plugins-ugly-doc
gstreamer0.10-plugins-ugly-multiverse
gstreamer0.10-plugins-ugly-multiverse-dbg

That didn't seem to work and I didn't have a lot of time to mess with this, so I installed all of these packages:

gstreamer0.10-plugins-base
gstreamer0.10-plugins-base-apps
gstreamer0.10-plugins-base-dbg
gstreamer0.10-plugins-base-doc
gstreamer0.10-plugins-farsight
gstreamer0.10-plugins-good
gstreamer0.10-plugins-good-dbg
gstreamer0.10-plugins-base-doc

mad must be included in one of those for the gstreamer 0.10.6 release currently in the ubuntu repositories, because it works now.

```

moodbar -o test.mood "test.mp3"
Analyzing file test.mp3
Received end-of-stream, exiting...

```

If I have time later, I'll try to narrow it down to the exact package necessary for decoding mp3 files for moodbar. I hope this helps other people that might be looking for a solution to this.

r4e

---

### Post by daniel_szollosi-nagy on 2008-03-10
I had the exact same problem but got stuck at not finding the mad plugin in the repositories. I can confirm that installing all of the ugly packages will display mood for MP3s. OGGs work out of the box.

Thanks for the tip, r4e

---

