---
title: "NVIDIA Binary Driver and Icon Themes"
date: 2010-08-25
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by computor on 2010-08-25
I apologise if this is a known issue, I haven't seen any threads about this...

I've had this problem for several weeks.  If I use the default video driver (nouveau), everything is fine (apart from compiz, general slowness, etc).  When I install the nvidia binary driver and reboot, the window decorations are fine, but the icons and the gnome-panel/widgets revert to the classic gnome theme (I think it's clearlooks, but don't quote me).  If I switch back to nouveau, everything is fine until the nvidia driver is re-installed.

I'm used to such anomalies in the development versions, but this one seemed especially strange as it has been this way for about a month now.  The problem actually went away a couple weeks ago and came back.  I know the current nvidia driver doesn't support the newer xserver in maverick yet (needs 'IgnoreABI', etc) and this may just be a symptom of that.  I just wanted to make sure I wasn't crazy as I haven't seen any other threads on this issue.

---

### Post by caryb on 2010-08-25
This has been documented pretty widely on this forum, my experience is that if I use the prop driver with ignore abi etc my laptop boots to 640x800 graphics. I tried to specify the mode in the xorg.conf but it ignores my settings.

Cary

---

### Post by MarkieB on 2010-08-25
no longer participating in ubuntuforums.org

---

### Post by cariboo on 2010-08-25
You have to run nvidia-settings as root in order to get the changes to stick press Alt-F2 and type:

```
gksu nvidia-settings
```

---

### Post by computor on 2010-08-25
When you say 'documented on the forum' are you talking about the icon theme issue or the resolution issue?

I used to have the resolution problem, but I think it was due to having an old .nvidiasettings.rc hanging around in my home folder.

I have no problems running the full 2560x1600 native resolution of my monitor with either driver--I just get the old, ugly icon theme unless I switch back to nouveau.

---

### Post by MarkieB on 2010-08-26
no longer participating in ubuntuforums.org

---

### Post by caryb on 2010-08-26
After todays updates (update to xorg-server) I installed the prop driver (via jockey) now my Nvidia works flawlessly without a xorg.conf


Cary

---

### Post by cariboo on 2010-08-26
The nvidia-settings item in the menus, only runs as the current user.

---

### Post by mc4man on 2010-08-26
There are 2 ways to save from nvidia-settings - one writes to /ect/X11/xorg.conf, (xserver settings), the other to ~/.nvidia-settings.rc (user settings

Don't see ant diff. in icons between nouveau and nvidia-current

---

