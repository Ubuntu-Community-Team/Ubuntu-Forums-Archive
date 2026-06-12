---
title: "mythbuntu frontend only display sleep problem"
date: 2009-09-11
forum: Mythbuntu
---

### Post by Eldis on 2009-09-11
I run mythtvfrontend using a script:
```
if [ ! "$(pidof mythfrontend.real)" ]
then
        echo "Mythfrontend is not started. Starting Mythfrontend..."
        DISPLAY=:0 xset -dpms
        DISPLAY=:0 mythfrontend --service
else
        echo "Mythfrontend is already started."

fi
```

I run this script by pressing a button on my remote I also run it on startup and when I resume from suspend or hibernate. My problem is that I have setup in xubuntu that my screen will turn off after 20 min idle, but I can't wake it up by pressing something on my remote. I can even start watching a recording or live tv but the screen won't wake up. If I attach a keyboard and press a button on that the screen will wake up.

So is there anything I could do with lirc and my remote that would tell it that it's time to wakeup from "idle". Maybe I'm running mythtvfrontend wrong with the script I'm using ? I can't confirm this but I think if I would start mythtvfrontend from the X directly using a mouse and keyboard i would not have this problem.

any help would be appreciated.

Using mythbuntu 9.04 and avenards VDPAU backport to mythtv 0.21

---

### Post by Eldis on 2009-10-10
Dunno what happened but I didn't change anything but this just started working one day. Must have been one of the updates.

---

