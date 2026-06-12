---
title: "small screen res with nvidia ag driver 173"
date: 2010-05-22
forum: Multimedia Software
---

### Post by Tehnoobguy on 2010-05-22
Yesterday i installed blender 2.49 in my Ubuntu 10.04. But when i started it and loaded the project I've been working on in Windows, blender started going really slow. I soon realized it was because of my video card.
I opened
> System>Administration>Hardware DriversIt told me there were two drivers i could install:
NVIDIA accelerated graphics driver (version 173),
and version 96.
version 173 was recommended so i thought, if i install this, everything will be fine :)
But i was wrong. After restarting, i found out that the screen resolution had become really low. I thought: No problem! I'll fix that...
Went into
> System>Preferences>DisplayI got the preferences window for the graphics driver.
There was a tab in which i could change screen resolution, but the highest res i could choose was 640x480. Same thing for version 96.

Any ideas what i can do? :confused:

---

### Post by ioi32 on 2010-06-02
It happens the same to me. Please, i need help!!!

---

### Post by tuffstuff on 2010-06-02
I think I can help.

You need to use the "nvidia X sever settings" dialog found in System -> Administration

I was then having an issue with the setting reverting after I rebooted. 

You can fix this by disabling "nvidia X server settings" from the start up applications menu in System -> Preferences

I hope this helps. I've been working on this a while.

---

### Post by Tehnoobguy on 2010-06-14
It doesn't work to change the resolution in x server settings...

---

### Post by Tehnoobguy on 2010-06-21
I installed a new video card, and it suddenly works :p
But now i'm having the same problem as you had, a reboot reverts the settings. 
There's no 'Nvidia X Server Settings' in my startup list. Is there any other way to fix it?


Btw, i have 9.10, not 10.04 as the first post says :lolflag:

---

### Post by wojox on 2010-06-21
In the terminal run

```
sudo nvidia-xconfig 
```

```
gksudo nvidia-settings
```

---

