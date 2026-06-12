---
title: "PixelView Play TV dmesg output not good"
date: 2006-01-11
forum: Multimedia &amp; Video
---

### Post by jcm88919 on 2006-01-11
I'm trying to get my pixelview playtv to work, which worked fine without sound before I tried to install ivtv thinking it was a tv program. Here is the output from dmesg. LSPCI shows my tuner, but apparently it isn't configured correctly because xawtv show no device at /dev/video0.
HELP!


 dmesg|grep bttv
[4294705.612000] bttv: Unknown symbol tveeprom_read
[4294705.613000] bttv: Unknown symbol tveeprom_hauppauge_analog
[4294705.839000] bttv: Unknown symbol tveeprom_read
[4294705.840000] bttv: Unknown symbol tveeprom_hauppauge_analog
[4294705.842000] bt878: Unknown symbol bttv_read_gpio
[4294705.842000] bt878: Unknown symbol bttv_write_gpio
[4294705.842000] bt878: Unknown symbol bttv_gpio_enable

---

