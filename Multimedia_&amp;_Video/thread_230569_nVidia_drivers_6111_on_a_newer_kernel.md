---
title: "nVidia drivers 6111 on a newer kernel?"
date: 2006-08-06
forum: Multimedia &amp; Video
---

### Post by Darth Tux on 2006-08-06
Hi everybody, well, after days of exciting fun trying to get my Radeon 9200 working correctly in Dapper I finally gave up and slapped in my Geforce 3 Ti 64MB AGP card, just to be hit with another problem. As it turns out, whenever I start a game or anything that takes any amount of rendering, that exceeds anything like glx gears, the screen goes blank and the monitor turns off. The entire computer locks up and nothing I do(ctrl+alt+bckspace, ctrl+alt+F*) can get me out of it and I am forced to do a hard-reboot. I did some googling to find out that this is a common problem with this card and that others fixed it by installing the 6111 drivers which work under anything <= 2.6.8kernel. Well, installing the 2.6.8 kernel didn't work for me and most of my peripherals stopped working and installing the 6111 drivers doesn't work under my 2.6.15-23 kernel. I even tried installing .deb packages of 6111 and that didn't work either. So, does anyone know where I can get a patch to install the 6111 drivers on >= 2.6.15, or does anyone have an idea to make this work with the later nVidia drivers? Keep in mind that I have also tried a whole lot of xorg.conf options to fix this and all of the suggestions have failed. Thanks for any response/help.

-darthtux

---

### Post by tseliot on 2006-08-06
Getting that driver to work might take a lot of patching (which is something that only Nvidia staff could do).

I suggest you to try installing the latest Legacy driver: 7182.

You can use my Envy script if you want.

---

### Post by Darth Tux on 2006-08-06
I appreciate it, and I did use your Envy script when I tried them. Nice job by the way, I also like the whole "invidia" meaning "envy" in italian thing, very clever. But the legacy drivers didn't work which is why I did a lot of research into it and discovered others with the same problem. They also couldn't get it to work with any amount of xorg.conf options and said that the latest driver that they could get to work properly was the 6111 driver.

---

### Post by tseliot on 2006-08-06
I think you should ask here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

### Post by Darth Tux on 2006-08-06
Yea, that kind of poses a problem for me being that I only have a gmail account and they do not accept free email accounts when registering. Though, if some kind soul that has an account and would being willing to spend a little time either searching or posting about my problem, it would be greatly appreciated. :D

---

