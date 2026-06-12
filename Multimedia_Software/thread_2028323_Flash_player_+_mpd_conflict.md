---
title: "Flash player + mpd conflict"
date: 2012-07-18
forum: Multimedia Software
---

### Post by Loser777 on 2012-07-18
This seems to be an age old problem I get with every Ubuntu install, virtual machine or on my desktop. Any time mpd tries to play something via alsa, it takes over the sound hardware and prevents sounds from being played by other applications. Mpd will refuse to play anything unless absolutely nothing else is using sound hardware. That is, if I start playing something in mpd sounds in other applications, say flash, will not be heard. If I start flash first, other programs will work fine but mpd cannot play anything. 

I've tried the various fixes, such as adding 
options "dev=dmixer"
device "plug:dmix"

or removing all of the configuration options other than type and name

or adding
mixer_type "software"

to the configuration. 

In the end, however, none of these fixes seem to change the problem encountered.

---

### Post by papibe on 2012-07-18
Hi Loser777.

Are you running mpd as root?
Could you post your configuration file?

This command should filter the relevant lines:
```
grep -v ^# /etc/mpd.conf | grep -v "^$"
```
Regards.

---

