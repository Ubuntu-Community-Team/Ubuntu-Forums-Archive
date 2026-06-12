---
title: "HDMI Sound on a Zotac G-E"
date: 2011-05-20
forum: Multimedia Software
---

### Post by rchille on 2011-05-20
Hello all!

I've been working on trying to get this little mini itx to output sound over the HDMI post off an on for about a year. I thought that with 11.04 I might give it another go.

I just did a fresh install and crossed my fingers....sadly no joy.

I've poked around the forums enough to grab the check ALSA script that lidex always links:

[http://www.alsa-project.org/db/?f=43d3fcbe132f773ff86f21068c8f6d7b271484c5](http://www.alsa-project.org/db/?f=43d3fcbe132f773ff86f21068c8f6d7b271484c5)

Other things:
I have checked to make sure none of my channels are muted via alsamixer

aplay -l doesn't seem to like my HDMI channel:

rob@r2d2:~$ aplay -D plughw:0,3 /usr/share/sounds/alsa/Front_Center.wav
aplay: main:660: audio open error: Device or resource busy

I'm hoping that this might be the issue, anyone know where to go from there?

Thanks!

---

