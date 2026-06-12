---
title: "nvidia-settings &quot;save to X configuration file&quot; kills xorg.conf"
date: 2007-06-26
forum: Multimedia &amp; Video
---

### Post by mr.v. on 2007-06-26
Hi all--

My search didn't find anything about this, but has anyone else noticed that when you save settings using nvidia-settings (run as superuser), that it completely destroys your xorg.conf file?!

It's unacceptable.

I noticed on my work computer, all of a sudden, my compiz had died. I couldn't figure it out. Everything was working one minute and suddenly my title bars wouldn't work. So I was frustrated and went back to metacity and was using that for a week or so.

Anyway, at home last night I did the same thing. I killed compiz. I realized I must have done something really screwy both times. The only thing was that came to mind was that I had run ```
sudo nvidia-settings
```  to adjust the color and refresh rate of my monitor to a higher level and saved my settings. Low and behold, an inspection of /etc/X11/xorg.conf revealed that Nvidia's own device manager removes ```
Option "AddARGBVisuals"        "True"
Option          "AddARGBGLXVisuals"     "True"
```
Even sillier, it also erases things like Input Devices, whether or not you have 3 button mouse emulation, a wacom tablet, and on and on.

Do they not realize that they can simply *modify* an xorg.conf file? Why must they completely rewrite it? Just readjust the settings under device, screen, and monitor, ensure there's no DRI module loaded, and leave the rest of the darn xorg.conf file alone. Fortunately, they make a backup file xorg.conf.backup, unless you happen to be a poor enough schmuck to go back into nvidia-settings and hit save *again* trying to fix a problem that nvidia-settings created in the first place...

---

### Post by dabl on 2007-06-26
Couple of comments:

nvidia-settings can only write to xorg.conf if you are running it in Super-User (sudo) mode.  So don't do that, unless you mean to overwrite the file.

I don't believe nvidia-settings has the capability to set the glx and compositing options.  That is done with nvidia-xconfig (when run in Super-User mode).  The relevant options are "--add-argb-glx-visuals" and "--composite"

---

