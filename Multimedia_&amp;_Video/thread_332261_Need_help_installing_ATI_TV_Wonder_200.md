---
title: "Need help installing ATI TV Wonder 200"
date: 2007-01-05
forum: Multimedia &amp; Video
---

### Post by phossal on 2007-01-05
I have the ATI TV Wonder 200. Has anyone had any success using it in Ubuntu? I would appreciate any assistance. I'm getting IO Permission errors and 'no tuner selected' statements when running TVTIME.

---

### Post by deadgobby on 2007-01-06
All I can find in wiki is this
[https://wiki.ubuntu.com/MythTVTeam/MythTVHardwareSupport?action=show&redirect=Testing%2FTVCapture#head-0528a3ae111660c328061e4b51fd975676ffaf2b](https://wiki.ubuntu.com/MythTVTeam/MythTVHardwareSupport?action=show&redirect=Testing%2FTVCapture#head-0528a3ae111660c328061e4b51fd975676ffaf2b)

I was going to get one. But it was not support and ATI did not have the linux drivers yet for it. But that was back at Breezy time.
Gobby

---

### Post by phossal on 2007-01-06
**[COLOR="#248"]Resolution[/COLOR]**

```
cd /etc/modprobe.d/
sudo echo "options cx88xx card=4 tuner=44" > cx88xx
modprobe -r cx8800
modprobe cx8800
```

The ATI TV Wonder Pro 200 isn't properly recognized. I was able to immediately run TVTime after executing these commands.

---

