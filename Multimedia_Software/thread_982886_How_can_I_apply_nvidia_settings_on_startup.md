---
title: "How can I apply nvidia settings on startup?"
date: 2008-11-15
forum: Multimedia Software
---

### Post by Sirron on 2008-11-15
When I first login, although I have 3D acceleration, settings I have made in the nvidia settings tool are not applied until after I have opened the tool.

Primarily, this bothers me for gaming, because I like to force antialiasing on, and currently I have to start the nvidia settings tool and close it again before starting a game.

I considered setting the tool to start when I login, but I don't want the GUI to show obviously - also, I would prefer the antialiasing to be turned on before Compiz Fusion starts, giving me a nicer looking desktop cube. I know that works, because I've run metacity --replace, then compiz --replace after opening the nvidia settings tool, and lo, the antialising was there.

I'm sure there's a solution, so thanks in advance!

---

### Post by aeiah on 2008-11-15
have you been running nvidia-settings as root to apply your settings? if not, it can't apply the settings to xorg.conf, although it seems it does still save the settings internally. try launching it with ```
sudo nvidia-settings
```

---

### Post by lovinglinux on 2008-11-15
I'm assuming you are running Ubuntu 8.10

I had the same issue.

Just add the following command to System >>> Preferences >>> Sessions

```
nvidia-settings -l
```

It will launch nvidia settings in the background, without the GUI, and your settings will be applied.

---

### Post by Sirron on 2008-11-16
Thanks, that's the main problem solved :), for games and the like - but it still seems to be loading after Compiz Fusion.

The only way I can think of solving that problem is to make Compiz Fusion start after the Nvidia settings tool, which would surely mean I'd have to set metacity as the default then switch to compiz fusion later.

That's a bit messy for my liking, I wonder, can I set the nvidia settings tool to start with the login manager or something?

---

### Post by lovinglinux on 2008-11-16
> **Sirron said:**
> Thanks, that's the main problem solved :), for games and the like - but it still seems to be loading after Compiz Fusion.

The only way I can think of solving that problem is to make Compiz Fusion start after the Nvidia settings tool, which would surely mean I'd have to set metacity as the default then switch to compiz fusion later.

That's a bit messy for my liking, I wonder, can I set the nvidia settings tool to start with the login manager or something?

I guess you have fusion-icon installed. So, remove fusion-icon and nvidia-settings from the Session. Then create a script with the following commands:
```

#!/bin/bash

nvidia-settings -l &
sleep 5 && fusion-icon
```

Save it and add it to the Sessions. When you reboot, this script will be launched and the commands will be run from it, not from the sessions. Since nvidia-settings is first in the command list it will load first. I have included a "sleep" command in front of fusion-icon just in case.

---

### Post by Sirron on 2008-11-16
No, I didn't have fusion-icon installed - but now I know of it, it's quite useful.

Looks like this script will let Compiz Fusion start, then launch the nvidia settings tool, then  reload Compiz Fusion when fusion-icon is launched.

Which is fine really, I'll see how it goes, thanks ^^

UPDATE:

Unfortunately when fusion-icon is launched, the screen flashes a lot, then Compiz Fusion randomly stops working unless I reload it.

If there's a script that launches compiz fusion in the first place, do you think I could stick

nvidia-settings -l &
sleep 5

at the top of it?

If so, where would I find this mystical script?

---

### Post by lovinglinux on 2008-11-16
> **Sirron said:**
> Unfortunately when fusion-icon is launched, the screen flashes a lot, then Compiz Fusion randomly stops working unless I reload it.

If there's a script that launches compiz fusion in the first place, do you think I could stick

nvidia-settings -l &
sleep 5

at the top of it?

If so, where would I find this mystical script?

Try this:

1 - uninstall fusion-icon

2 - replace the script with the following code:

```
metacity --replace
nvidia-settings -l
compiz --replace
```

I can't test this script right now, because I can't logout. Theoretically, it will replace the window manager with metacity, then it will load nvidia settings and then replace the window manager with compiz again. I just don't remember if this works without sending the commands to the background. So please tell me it works, otherwise I will try something different.

---

