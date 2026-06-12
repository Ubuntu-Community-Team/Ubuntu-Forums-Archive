---
title: "Need help setting up IR Blaster to turn on/off the TV"
date: 2008-09-01
forum: Mythbuntu
---

### Post by bmwman on 2008-09-01
I need help setting up IR Blaster to turn on/off the TV whenever I turn on the MythTV. Basically I have this remote :
[http://www.newegg.com/Product/Product.aspx?Item=N82E16880121003](http://www.newegg.com/Product/Product.aspx?Item=N82E16880121003)

I programmed all the buttons that I want and it works great with MythTV. I haven't set up the power button yet. I would like to be able to push the power button and put the computer on Stand By or resume it from stand by and start the Frontend. Also If it's possible to turn on/off the TV at the same time the computer turns on via IR blaster which I have but have never used it.

Any suggestions how to achieve that?

Thanks in advance.

---

### Post by bmwman on 2008-09-02
Can somebody point me in the right direction at least how to put the PC on Standby and resume from inside MythTV for starters?

---

### Post by volkswagner on 2008-09-02
> **bmwman said:**
> Can somebody point me in the right direction at least how to put the PC on Standby and resume from inside MythTV for starters?

These treads may help.  First you may need to decide if suspend is right for you.  I am not sure how the pc will resume for recordings (if you have a backend running on this machine).

[http://ubuntuforums.org/showthread.php?t=616476&highlight=sleep+remote]("http://ubuntuforums.org/showthread.php?t=616476&highlight=sleep+remote")

[http://ubuntuforums.org/showthread.php?t=665111&highlight=sleep+remote]("http://ubuntuforums.org/showthread.php?t=665111&highlight=sleep+remote")

[URL="http://ubuntuforums.org/showthread.php?t=680312&highlight=sleep+remote"

[http://ubuntuforums.org/showthread.php?t=675455&highlight=sleep+remote]("http://ubuntuforums.org/showthread.php?t=675455&highlight=sleep+remote")

---

### Post by bmwman on 2008-09-03
Thanks for the info. Actually i was going by this How To:
[https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake](https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake)

I guess I need to set my HTPC to turn off and wake up automatically first. I did everything up to the point where you have to edit  ~/.config/autostart/mythtv.desktop and change Exec=mythfrontend to Exec=mythwelcome. I did that and restarted. After that not only the Mythwelcome didn't start (btw i don't think I've ever seen how it looks like), but even the Frontend doesn't start automatically either. I changed it back to Exec=mythfrontend but still doesn't work. Actually the whole Frontend shortcut dissappeared from the main menu. It was under Applications-Multimedia. On top of that the computer kept shutting off by itself after couple of minutes every time I rebooted. WTF

So I went back and cancelled all the changes that I did so now my PC doesn't shut off by itself whenever it feels like but I still can't get the frontend to start automatically after reboot. I'm not exactly sure how is this supposed to work. I do want to have the PC turn on automatically if there is a scheduled recording comming but I definetly don't want it to shut off by itself. I need to set up the Power button on my remote to shut it off but I don't know how to do that.

Any guidance is welcome.

---

