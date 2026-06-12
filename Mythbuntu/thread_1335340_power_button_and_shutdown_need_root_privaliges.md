---
title: "power button and shutdown need root privaliges"
date: 2009-11-23
forum: Mythbuntu
---

### Post by My Name on 2009-11-23
Hi All,
Loving the new 9.10 mythbuntu BTW, but one small problem. i used to use the power button to shut the computer down, but now it asks me for the root password to shut down. 
I think this is the reason for the shutdown option in the mythbuntu menu to be unresponsive. 
my previous mythtv installation was mythdora, as it seemed to me, with my hardware to be the most stable. I am aware that mythbuntu uses xfrce as it's desktop environment, whereas mythdora uses gnome.
I don't know my way around xfrce as well as gnome but i can't find any option to add shutdown privaliges to a standard user.

Any ideas?

Thanks in advance

---

### Post by ian dobson on 2009-11-23
Hi,

Have a look here:- [http://www.linuxquestions.org/questions/linux-newbie-8/how-to-edit-sudoers-file-using-visudo-597400/](http://www.linuxquestions.org/questions/linux-newbie-8/how-to-edit-sudoers-file-using-visudo-597400/) to allow normal users to shutdown/reboot a system.

Regards
Ian Dobson

---

### Post by dibuntux on 2009-11-23
No shutdown privilege - Ubuntu desktop with mythbuntu .. extra session issue
try this, it worked for me

create a new file with:

sudo nano /var/lib/polkit-1/localauthority/50-local.d/shutdown.pkla

paste inside this:

[system shutdown privs]
Identity=unix-group:users <-- your users group here
Action=org.freedesktop.consolekit.system.stop-multiple-users
ResultAny=no
ResultInactive=no
ResultActive=yes

then create this too:
sudo nano /var/lib/polkit-1/localauthority/50-local.d/restart.pkla

and paste this:

[system restart privs]
Identity=unix-group:users <-- your users group here
Action=org.freedesktop.consolekit.system.restart-multiple-users
ResultAny=no
ResultInactive=no
ResultActive=yes

taken from: [http://wiki.archlinux.org/index.php/...leges_to_Users](http://wiki.archlinux.org/index.php/...leges_to_Users)

---

### Post by My Name on 2009-11-24
I'll give these a try and post back the results.  Cheers

---

