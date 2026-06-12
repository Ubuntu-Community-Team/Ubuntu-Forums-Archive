---
title: "nvidia dual monitor support with HDTV"
date: 2007-07-23
forum: Multimedia &amp; Video
---

### Post by eqisow on 2007-07-23
I'm trying to set up my computer to output 1680x1050 to my 22" LCD and 720P to my 30" HD CRT. I'm using the latest Feisty nVidia drivers with a GeForce 6800. The LCD is connected via D-Sub/VGA and the TV is connected by DVI.

nvidia-settings configured everything OK, except that it seems to think my TV can only support NTSC 640x480. Since I can't figure out how to get around that, I've been editing my xorg.conf manually. I've set 720p as the only available resolution for the TV, but it seems to still be 640x480. Also, the Display Settings in System Settings crashes when I try to select it, which makes me think perhaps nvidia-settings is overriding my xorg.conf somehow.

I have attached my xorg.conf file.

Edit: Played with Xorg.conf some more, and attached current Xorg.conf. Same result as before.

I think the nvidia-settings problem is because the EDID on my TV is not accurate.

---

### Post by MrHippocampus on 2007-07-25
I glanced over your xorg.conf and nothing is jumping out at me. You could try searching/asking on the nvidia linux forum, [nvnews linux forum]("http://www.nvnews.net/vbulletin/forumdisplay.php?f=14").

---

