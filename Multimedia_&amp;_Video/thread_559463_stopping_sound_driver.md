---
title: "stopping sound driver"
date: 2007-09-25
forum: Multimedia &amp; Video
---

### Post by rohit raj on 2007-09-25
i have realtek alc880 sound card .Ubuntu detects the sound card but full sound does not comes from speaker .I have tried alsamixer , volume settings are maximum .Then i installed the latest version of alsa  ,alsa 1.0.14 . But still problem didn't got solved .Its my guess that its probably due to alsaconf not being able to stop sound driver  as it says something like this 

                                                             &#9474;                               
                               &#9474;   If ALSA is already running, you should close all sound    &#9474;                               
                               &#9474;   apps now and stop the sound driver.                       &#9474;                               
                               &#9474;   alsaconf will try to do this, but it's not 100% sure.     

After configuring the driver through alsaconf i don't hear anything when it plays some test file
any ideas ?

---

### Post by overdrank on 2007-09-26
> **rohit raj said:**
> i have realtek alc880 sound card .Ubuntu detects the sound card but full sound does not comes from speaker .I have tried alsamixer , volume settings are maximum .Then i installed the latest version of alsa  ,alsa 1.0.14 . But still problem didn't got solved .Its my guess that its probably due to alsaconf not being able to stop sound driver  as it says something like this 

                                                             &#9474;                               
                               &#9474;   If ALSA is already running, you should close all sound    &#9474;                               
                               &#9474;   apps now and stop the sound driver.                       &#9474;                               
                               &#9474;   alsaconf will try to do this, but it's not 100% sure.     

After configuring the driver through alsaconf i don't hear anything when it plays some test file
any ideas ?

HI maybe this thread will be of some help
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
Good luck!

---

