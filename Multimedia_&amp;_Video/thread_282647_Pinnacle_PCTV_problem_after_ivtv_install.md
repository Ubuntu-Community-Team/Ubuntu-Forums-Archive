---
title: "Pinnacle PCTV problem after ivtv install"
date: 2006-10-23
forum: Multimedia &amp; Video
---

### Post by arkoudi on 2006-10-23
Hi ppl,
I'm new to ubuntu and I'd like some help if it is possible.
I have a pinnacle pctv card and I have a problem with the bttv driver.
[17179589.212000] bttv: Unknown symbol tveeprom_read
[17179589.212000] bttv: Unknown symbol tveeprom_hauppauge_analog
[17179589.244000] bttv: Unknown symbol tveeprom_read
[17179589.244000] bttv: Unknown symbol tveeprom_hauppauge_analog
[17179589.276000] bt878: Unknown symbol bttv_read_gpio
[17179589.276000] bt878: Unknown symbol bttv_write_gpio
[17179589.276000] bt878: Unknown symbol bttv_gpio_enable

This all started after I tried to install IVTV 4.0 in favor of the radio capability of my card cause with bttv I could not make it work.

I did some googling for this problem that others also had, but I could not understand how to fix it. I lost somehow some modules like tuner.ko etc

Then I tried to recompile my kernel so the bttv module would work again, but I have a kernel panic issue after the recompiling (after doing the recompile through an Ubuntu guide).

Problems that I found in favor of a radio card (lol).

Can anyone help me with this? Cause as you see I'm a complete n00b :P I can read guides if you have any to suggest me, but it seems through the guides I read that ubuntu does not work like other distros so I cannot make it work for now.

I forgot to mention that I use Ubuntu 6.06 LTS Dapper Drake :)

Thanks for you time reading this post :)

---

