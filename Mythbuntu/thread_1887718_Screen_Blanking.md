---
title: "Screen Blanking"
date: 2011-11-27
forum: Mythbuntu
---

### Post by mitchell2345 on 2011-11-27
Hi,

I am running the latest version of mythbuntu.  Wondering how i can disable screen blanking.  Whent the frontend is idle the screen goes blank and all too often the TV doesnt get shutoff and it sits for a day.

Suggestions?

Thanks,
Mitchell

---

### Post by klc5555 on 2011-11-27
There are a few methods at least. Sometimes one works depending on how x is installed and configured, sometimes another.

Easiest for a normal myth on top of xfce installation ought to be to go into the xfce settings menu to screensaver, and in the "mode" setting set to "disable screen saver".

If this doesn't work, maybe the command "xset -dpms s off" will do the job for you. I suppose that if necessary a startup 'application' could be added to xfce in the startup app menu that would consist of the single line "xterm -e xset -dpms s off"

---

