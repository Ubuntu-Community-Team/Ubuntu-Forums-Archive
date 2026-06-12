---
title: "Can't display over 1024x768"
date: 2006-12-29
forum: Multimedia &amp; Video
---

### Post by GoldenChaos on 2006-12-29
I was finally going to make the switch to Linux with Ubuntu, knowing that I've had good experiences with it in the past, but after dual booting it and trying it out, it might not be worth all of this trouble. You see, I can't even get this thing going past 1024x768 resolution. I can't even put the refresh rate over 60Hz.

I thought it might have been a problem with the nVidia drivers (I'm running a GeForce 7800GTX), but after going through every process I could find, nothing worked. I couldn't even get the little nVidia settings thing to appear anywhere. (In fact, it seems NOTHING I install shows up in the applications menu... how come?)

Ubuntu has also frozen twice since I installed it last night. I was really, really excited about the whole "Just Works" thing. Why do I have to go into a terminal if it "just works"? Can anything be double-clicked and installed? o_O

Anyways, right now I just want to get it running at 1280x1024, 75Hz. If it can do that, more power to Ubuntu. Please help in any way possible - thank you!

---

### Post by s6dalane on 2006-12-29
You can generate a modeline for your monitor from [here]("http://www.sh.nu/nvidia/gtf.php").

> x: 1280, y:1024, refresh: 75

Then you need to add this to your xorg.conf file (sudo gedit /etc/X11/xorg.conf) to the following line:

> Section "Monitor"
    Identifier     "CM721F"
    Option         "DPMS"
    Modeline "1024x768_115.00"  131.43  1024 1096 1208 1392  768 769 772 821  -HSync +Vsync
EndSection

---

