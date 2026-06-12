---
title: "[SOLVED] 8.04 - Changed Monitor Res. reverts back to Former Res. on Login &amp;amp; Restart"
date: 2008-12-04
forum: Multimedia Software
---

### Post by kilroy0097 on 2008-12-04
There are many different posts on people having issues with monitor resolutions sticking and I believe I've done just about all that I know how to do at this point.

Problem: Got a new LG W2600H monitor that is capable of much higher resolutions. So I attempt to change the resolution to something higher.

My steps:
terminal - su root - nvidia-settings 
Go in and change monitor resolution from "1400x1050" to "1920x1200" refresh rate 60. (Get the same settings if I choose Auto)
Apply and Save X Configuration Changes.
Confirmed change in /etc/X11/xorg.conf file visually via terminal
Logout and Login or Restart and Login.

Conclusion: Resolution returns to previous 1400x1050 state and I must manually set it back to the prefered 1920x1200

A Copy of my */etc/X11/xorg.conf* file and my */var/logs/Xorg.0.log* file are attached to this post.

I have attempted *sudo dpkg-reconfigure xserver-xorg* to default the xorg.conf settings and renew them fresh but that didn't help.

-

The only thing that jumps out at me are the last two lines in the Xorg.0.log file:

> (II) NVIDIA(0): Setting mode "1400x1050"
(II) NVIDIA(0): Setting mode "1920x1200_60+0+0"

So it's some how calling that old resolution from somewhere. When I check nvidia-settings -> GPU 0 - (GeForce 7300 LE) -> DFP-0- (LG W2600) it will show the Native, Best Fit and Backend Resolutions correctly at 1920x1200. However the Frontend Resolution will show 1400x1050. No where else do I see evidence of where or why it's defaulting to 1400x1050.

Any help would be much appreciated.

Cheers.

---

### Post by eternalnewbee on 2008-12-04
I've got a twenty inch monitor and have Geforce7300GT installed.
My highest possible resolution is 1600 x 900 (16:9), and the refresh rate is set at 51 Hz.
Only thing I can think of is try to safe your session, and see if that makes any difference.
Go to: **Main Menu > System > Preferences > Sessions > Options** tab, and click **Save Currently Running Applications**.

---

### Post by atomizer on 2008-12-04
maybe you can change /etc/X11/xorg.conf manually....
ofcourse you have to backup your xorg.conf first

      ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

then change some lines

     ```
sudo nano /etc/X11/xorg.conf
``` (or use your favorite editor instead of nano)

```
Section "Screen"

    Identifier     "Screen0"

    Device         "Videocard0"

    Monitor        "Monitor0"

    DefaultDepth    24

    Option         "TwinView" "0"

_#    Option         "metamodes" "1920x1200 +0+0; 1920x1200_60 +0+0"_

    SubSection     "Display"

        Depth       24
        _Modes      "1920x1200"_
    EndSubSection

EndSection
```

if it doesnt work, you have to change your xorg.conf back to the old one and find another solution.
    ```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

---

### Post by kilroy0097 on 2008-12-04
Thank you for the quick reply!

The monitor I have (LJ W2600H) is a 25.6" monitor. Native resolution is 1920x1200 at 60hz refresh.

Though it's an odd fix, your suggestion helped. When I logout and login it now keeps the 1920x1200 resolution. One would think if you could save a session with the correct video resolution, that you could make it a default someplace as well.

There is one odd thing though. 
**Main Menu > System > Preferences > Screen Resolution**

It shows the monitor graphic with "Unknown" in the middle of it even though it shows the Resolution correctly at 1920x1200. However the Refresh Rate is set at 51hz instead of 60hz. Not sure if that has anything to do with the original issue.

Where does Screen Resolution from that menu get it's data from? Perhaps there is different .conf file of a video nature that it reads instead of xorg.conf. If so that might be the root of the issue.

Thanks again. :D

Edit add:
atomizer, thank you also for the reply. I will give your suggestion a try if Session Manager doesn't work in the future.

---

### Post by eternalnewbee on 2008-12-04
> It shows the monitor graphic with "Unknown" in the middle 
Same here. Just guessing it's because the resolution is set higher than default. Again, just guessing.
If Atomizer's method works, that's excellent, but out of my league...
Anyways, glad it worked out for you.
Btw, if you feel your problem is solved, please mark the thread as solved, under Thread Tools, at the top of this page.
See you around the forums.):P

---

