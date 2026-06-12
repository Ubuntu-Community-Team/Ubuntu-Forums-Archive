---
title: "Media Centre via Command Line"
date: 2008-04-05
forum: Multimedia &amp; Video
---

### Post by kiiadi on 2008-04-05
Sorry if this has been posted before but I've had a hunt around and I can't find anything similar. What I'm looking to create is a media centre controlled via a web-interface ideally or alternatively by command-line.

I have Ubuntu 7.10 running on a box which is connected directly to my TV (via VGA out). I'd like to be able to essentially queue up what's playing on the TV, from my couch (via SSH or HTTP) without having to log in and start videos via the GUI.

Is there anything out there that allows me to do that? How can I start VLC at command line but tell it to appear on the main screen physically connected to the box?

I'm a bit of a newb with this sort of stuff so apologies if this seems like a stupid question!

---

### Post by tamoneya on 2008-04-05
taking a quick look at vlc --help i would suggest you use the vcd:// url.  Depending on what your using for your video in the url will change.  Also use the -f option to place it in full screen ```
vlc vcd://dev/dvb -f
``` This uses /dev/dvb as your video device which is a common device for TV tuners.

---

