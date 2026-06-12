---
title: "Hardy DVB install - big problems!"
date: 2008-05-08
forum: Multimedia Software
---

### Post by harleym on 2008-05-08
I have a DVB box with a DVICO Fusion Dual 4 DVB-T card and an NVidia Geforce 6150 which were all working fine under Feisty using the nvidia drivers. I upgraded to gutsy and then hardy and then recompiled the v4l-dvb as per the linuxtv.org DVB Wiki just as I had done with Feisty kernel upgrades and the machine failed at the hardware initialisation step and prevent the video from working at all. I upgraded to the latest v4l-dvb source, recompiled and the same thing happened. 

After spending a day trying to remove the offending drivers, and thinking the dist-upgrade process may have problems, I gave up and did a clean install of Hardy and got all the NVidia video working nicely. I then downloaded the source to v4l-dvb, compiled, installed and the boot process failed at the exact same spot (you may see a pattern here).

So back to reinstall Hardy and doing without DVB until the problem can be resolved. I followed the steps listed on the page [https://help.ubuntu.com/community/DViCO_Dual_Digital_4](https://help.ubuntu.com/community/DViCO_Dual_Digital_4) and the problem happened anyway.

It is not one of the new revision cards that have caused problems as it was working fine under Feisty.

I will partimage next time before trying the v4l-linux installation, as reinstalling is getting tedious. I would like my DVB back...

Any ideas on how to fix this?

Regards,

Harley

---

