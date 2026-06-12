---
title: "go 6150 nvidia card noveau vs nvidia driver for online video?"
date: 2013-05-02
forum: Multimedia Software
---

### Post by sdowney717 on 2013-05-02
the laptop is not upgradable and online video is pretty terrible.
I am currently using the nvidia driver version 306?.
would it work better using the free noveau driver for flash and html5 type online video?
i upgraded to kernel 3.9 which i read has improvements in the free driver

i dual boot with win7 and i noticed the online video is much much better in safe mode vs normal mode. I also have the nvidia driver installed in windows 7
ver 186.22

my suspicians is driver programmers donbt care about older hardware, so the available drivers have been designed to work with faster hardware. otherwise how could windows in safe mode have so much better video?

---

### Post by sdowney717 on 2013-05-03
glxgears testing 

with nvidia driver 500 frames 60fps
with noveau driver 500 frames 120 fps

anyway watching online video was not better with noveau driver, in fact looked like it made zero difference between it and nvidia driver.

In win7 a selective startup may have improved win7 playback. at least it does not jerk so much.

WOULD running an older version of the nvidia driver improve the performance in Ubuntu?
, 
also 480p is watchable in windows, ubuntu stutters at 480p and for 720 forget it

---

### Post by monkeybrain2012 on 2013-05-03
flash is always kind of horrible. If you are just watching videos on popular sites maybe you should use a flash replacement.

[http://userscripts.org/scripts/show/87011](http://userscripts.org/scripts/show/87011)
and/or
[http://linterna-magica.nongnu.org/](http://linterna-magica.nongnu.org/)

Use gecko-mediaplayer plugin  in FF and adjust video output to vdpau in gnome-mplayer to get hardware accelerated decoding if you are using the Nvidia blob.

---

### Post by sdowney717 on 2013-05-04
i dont know whether to pursue ubuntu on this laptop anymore. in regards to improving the video experience.

I upgraded in win7 to ie10. laptop did a massive amount of windows updating.
now the video plays smoothly in windows upto 480p.
so windows 7 did something to improve video for html5 and the flash player.

i tend to like using chrome. I have a feeling that ubuntu video on this older laptop will never improve.
In windows using msi afterburner, i was able to overlock the video card. the nvclock program in ubuntu is broken.

i think if i could do a similar overclock in ubuntu, the video might be good enough.

---

