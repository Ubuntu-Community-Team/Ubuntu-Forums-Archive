---
title: "HOWTO: nvtv workaround"
date: 2007-06-09
forum: Multimedia &amp; Video
---

### Post by puterboy on 2007-06-09
After searching for a way to configure TV-Out, I found nothing that worked, so here is my own howto after I got mine working.

Card: NVIDIA 6600GT
Ubuntu 6.06 Dapper Drake AMD64



First off, i didn't end up use nvtv. i used envy, which configured all my settings for me. maybe it's cheating, but whatever.....after it installed the packages and stuff i needed, nvtv STILL wouldn't work, despite finally seeing the NVIDIA splash screen. so I went into 

Applications>System Tools>NVIDIA X Server Settings

I went to the X Server Display Configuration, clicked on my TV (which it had never detected before), and configured it (I put my screen to the right of screen 0, my PC monitor. I couldn't apply settings, so I saved it and restarted. It didn't work after restarting my X Server (Ctrl+Alt+Shift+Backspace). I found that the file didn't have the correct permissions, so i used

sudo chmod a+rwx /etc/X11/xorg.conf

to let me write it. I couldn't seem to keep any settings by overwriting the file, so I had to save the xorg.conf from the settings panel on my desktop, open both, and paste over the contents of the old file with the new one. worked like a charm. i'm so newbish, but it works now. any questions, feel free to PM me, i'll try to help as much as I can.

Also, after every reboot of the X server, you need to reconfigure your TV setting in the panel, because if it didn't work, it'll overwrite the settings to where your TV is disabled.

Hope it works!!!

---

