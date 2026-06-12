---
title: "Help problems with my AMD rx 560 graphic card"
date: 2019-01-15
forum: MINT
---

### Post by azmo35 on 2019-01-15
Hi first let me tell that the problem is on Linux Mint 19.1 fresh install with open source driver, kernel 4.15.0-43, xserver-xorg-core 2:1.19.6-1ubuntu4.2 amd64, but booting up pc I'm stock at [https://i.postimg.cc/HLygHKbW/IMG-20190115-165618796.jpg](https://i.postimg.cc/HLygHKbW/IMG-20190115-165618796.jpg) this image freeze, if I use reset on pc it will boot just fine, since this is Mint and not Ubuntu I can't install proprietary drivers to see if improves, thanks for any help.

---

### Post by wildmanne39 on 2019-01-15
*Thread moved to **MINT for a more appropriate fit**.*

Please use the attachment facility by clicking on the paperclip or  use url's for images because apart from bandwidth issues for some, it makes it difficult for those using mobile devices to browse the forum.

---

### Post by QIII on 2019-01-15
From your image and what you describe, I'm going to suggest to you what I just suggested to another user:

Before you work on possible driver issues, use the "rule-out" branch of diagnosis and eliminate a hardware fault in the monitor itself. What you show there and your description of the behavior might indicate loose connections or a monitor that is about to spew blue smoke.  By rebooting the machine, you have also interrupted and restored the video signal to the monitor.  Let's see if that is the source of the behavior.

First check and double check the connections.

From that starting point, do the following the next couple of times this happens:

Either disconnect and reconnect the video cable or cycle the monitor power.

---

### Post by azmo35 on 2019-01-15
To wildmanne39 sorry for posting wrong at long time I don't use the forum,
To QIII Graphic card is 2 months old Cable is new and is connected DP to HDMI and TV is 6 months old and HDMI to HDMI do the same, on Mint 19 I add Oibaf drivers but at on boot I got a black screen, I got frustrated and done a fresh install Mint 19.1 to get back the default  open source driver, thanks for help.

---

### Post by wildmanne39 on 2019-01-15
No apologies needed.:)

---

### Post by azmo35 on 2019-01-17
Hi boot pc with tv off it works without a problem but I get a crackling sound and using this command "pulseaudio -k && sudo alsa force-reload" don't fix the crackling but using "sudo pm-suspend" fix it, but it like still related to the graphics or driver, thanks for any reply.

---

