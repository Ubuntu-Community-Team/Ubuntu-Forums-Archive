---
title: "ati driver question"
date: 2006-06-09
forum: Multimedia &amp; Video
---

### Post by hellseeker on 2006-06-09
i have an ati igp 320m on my presario 2100 laptop, i noticed the video is not as good as it could be so i figured i should install the drivers from the ati web site. i downloaded the mobile drivers. now im completely lost. can any1 explain to me how to install these?
thanx

---

### Post by eurika on 2006-06-15
Only the "radeon" driver can be use on this 3d card ... 
Change in your xorg.conf "vesa" by "radeo"

I have the same computer :D

---

### Post by liches on 2006-06-17
I have the same computer as well (Compaq Presario 2100) runing Ubuntu 6.06 LTS.
Direst Rendering worked out of the box with Breezy, but I've been having a lot of trouble with Dapper.
The driver in my xorg.conf file is set to radeon, but I still don't get direct rendering. Are there any other modules I need to download, start at startup, or other config files that need to be changed for me to get the same functionality i had with Breezy with the radeon driver?

Please help, I'm mostly a newb.

---

### Post by yzord on 2006-06-17
Hey there,
Being in a somewhat similar position, I dug around for ways to optimize screen performance. I tried adding a few more entries to the /etc/X11/xorg.conf file:

Under 'Section "Device"'
Option "RenderAccel" "True"
> unfortunately, for me, this this makes buttons get graphically distorted under the "Human" theme, so I had to put it back to "false"
Option "AGPMode" "4"
Option "EnablePageFlip" "true"

The above pushed my glxgears ("glxgears -printfps") from ~280s to 860s. More importantly, a "glxinfo | grep direct" indicated "direct rendering: Yes". I also installed driconf ("sudo apt-get install driconf") to tweak TCL Hardware rendering and to turn on HyperZ (these two are 3d enhancements, and should have no affect on direct rendering, but I feel compelled to indicate them in case driconf made some difference).

Yz

ps. I have an X31 with a Radeon 7000 (Mobility M1)

---

### Post by Anthem on 2006-08-19
> **yzord said:**
> ps. I have an X31 with a Radeon 7000 (Mobility M1)
My understanding is that the Radeon7000 is fully supported by the open-source Radeon driver, but the 320m is not.  Am I incorrect in this?

---

