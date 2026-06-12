---
title: "2 displays, 2 X servers: which one would be selected by default after reboot?"
date: 2007-06-21
forum: Multimedia &amp; Video
---

### Post by volenin on 2007-06-21
Hi,

I have the following configuration:

1) nVidia video card with TV-out
2) xorg with two layouts:
    a) 'default', outputing to attached monitor
    b) 'TV', outputing to TV
3) kdm started up at system bootup on display :0
4) freevo started up on a separate X server on display :1

Currently I'm starting up freevo (and its X server) manually after system boots up, but eventually I want to put freevo either in Upstart scripts or in rc.local. I also want to have kdm on this machine for a while to fine tune some configurations, etc.

So, what I want is to have Ubuntu switch to 'freevo' X server (TV output) at system bootup, instead of the KDM (monitor output). Currently KDM X server is running on display :0, tty7, while manually started freevo x server - on display :1, tty9. So, to reiterate, for the configuration above, where both x servers are started at system reboot, which display will get automatically selected? :0? or there is some particular rule/config file that defines it?

Thanks,

Vlad

---

