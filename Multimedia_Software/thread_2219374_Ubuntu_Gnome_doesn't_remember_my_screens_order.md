---
title: "Ubuntu Gnome doesn't remember my screens order"
date: 2014-04-23
forum: Multimedia Software
---

### Post by Laurent_Dinclaux on 2014-04-23
Hello,

I tried either using Nvidi or the Nouveau drivers. After each reboot I have to setup my screens order ans positions that are forgotten after each boot.

I tried using the Gnome settings and nvidia-settings.

Regards

---

### Post by martin-dueren on 2014-05-04
Did you find a solution? I have the exact same problem!

Edit: Never mind I found a work-around! This seems to be a known bug. A work around is to have this command as a start-up-application :
> pkill -9 -f gnome-settings-daemon

---

