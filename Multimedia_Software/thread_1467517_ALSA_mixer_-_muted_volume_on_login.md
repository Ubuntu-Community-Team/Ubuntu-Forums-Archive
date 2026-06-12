---
title: "ALSA mixer - muted volume on login"
date: 2010-04-30
forum: Multimedia Software
---

### Post by Psimon on 2010-04-30
This is a problem I had on Karmic, and I still have it after a fresh install to Lucid Lynx.

When I log in there's no sound - I had to install gnome alsa mixer in order to unmute them. But the next time I log in the volume is muted again. My settings are not being saved when logging out.

I've tried various solutions found on the forums but so far nothing has worked. It's only a minor annoyance but I love to see the back of it.

Any ideas?

---

### Post by Yellow Pasque on 2010-04-30
```
gksu gedit /etc/rc.local
```
Add this line before the 'exit 0' line:
```
amixer set Master unmute
```
The channel name may be different than Master, so check in alsamixer.

---

### Post by Psimon on 2010-04-30
Thanks foryour reply.

I did as you said but it made no difference.

When I open gnome alsa mixer after log in the 'Master M' channel is set to mute.

Do I need to modify that line?

---

### Post by velko on 2012-06-04
what I did was purge and  install all my alsa packages again.

Like this:

sudo aptitude search "alsa" | grep "^i"

i   alsa-base                       - ALSA driver configuration files           
i   alsa-oss                        - ALSA wrapper for OSS applications         
i A alsa-utils                      - Utilities for configuring and using ALSA  
i   alsamixergui                    - graphical soundcard mixer for ALSA soundca
i   gstreamer0.10-alsa              - GStreamer plugin for ALSA


Then I do a :

sudo aptitude purge alsa-base ..... all of them


then  I do:

sudo aptitude install alsa-base ... the same packages...


and after several test reboots all works..

ubuntu 12.04 - latest updates on a Dell l502x aka xps 15.


--

This worked nicely.

I prolly managed to mess up my settings/rc-scripts while trying all those fixes in the recent months...

---

