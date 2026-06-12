---
title: "Enabling SVIDEO on NVIDIA"
date: 2007-07-16
forum: Multimedia &amp; Video
---

### Post by yousufn on 2007-07-16
i realize this might be a bit of a noob post however as a new user, I like many others have had a lot of issues with getting SVideo out functioning properly with my NVidia GeForce 7600GS (running feisty on an intel chip). I thought putting up my logs might help out other people who seem to be going through the same thing. btw many thanks to tseliot for his numerous nvidia related posts which really helped. in the end i did have to edit my /etc/X11/xorg.conf in the following manner. 

on a sidenote please dont begin before making a backup of this very integral GUI config file through the following command: $sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup. This way in case of a catastrophe you can replace the original by flipping the arguments for the cp command in the terminal (i.e $sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf) Once this has been done open up the file for editing by: $sudo nano /etc/X11/xorg.conf

Though i began by editing several sections of xorg.conf in the end only one proved to be helpful. The rest gave me a variety of obscure errors which claimed to have misplaced my NVidia kernel, drivers, etc.. never did end up figuring that one out. In any case here's a copy of Section "Screen", the relevant bits anyways. 

Option	   "TwinView"
    Option	   "SecondMonitorHorizSync" "30-50"
    Option	   "SecondMonitorVertRefresh" "60"
    Option	   "MetaModes" "1280x1024,800x600;1024x768,800x600;832x624,800x600;800x600,800x600;720x400,800x600;640x480,800x600"
    Option	   "TwinViewOrientation" "RightOf"
    Option 	   "TVOutFormat" "SVIDEO"
    Option	   "Connected Monitor" "CRT,TV" 

These are the lines i added under the "Screen" Section the TwinView option enables the nvidia drivers to feed output to two displays. The values for the horizsync and vertrefresh are fairly standard for most TVs. The orientation option is self-explanatory. The TVOut option can also be set to "COMPOSITE" if applicable. Finally the Connected Monitor option, the use of which is self-evident. I left the MetaModes for last because they seem the most cryptic but really they're not that complicated. They're merely used to synchronize the resolution of your TV with whatever you've chosen for your Monitor so that whenever you choose a resolution for your primary display, xconf already knows what to do with your secondary display.

However, please note this is a quick fix. though i finally got my Video Card to start using my TV, there are a few problems i.e. my wallpaper is stretched out over two screens! so yeah... it works but not too well. however ill be sure to post a fix for that as soon as i figure it out. (and if anyone else knows what i'm doing wrong, help!) gl...

-Yousuf

---

### Post by yousufn on 2007-07-16
sorry forgot one really imp. thing, dont just use my entries from the MetaModes field, you have to find out whats applicable for you. A quick scan through the display subsection of xorg.conf should do it...

---

