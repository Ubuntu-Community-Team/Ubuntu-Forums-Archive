---
title: "Gnome-Shell Kills Mythbuntu Display"
date: 2013-01-24
forum: Mythbuntu
---

### Post by Cerin on 2013-01-24
I installed Mythbuntu on a vanilla Dell Inspiron 660s desktop connected to an HDMI monitor, and most everything seemed to work.

However, after having used Gnome-Shell for a couple years, I hate the restricted UI of XFCE. So I installed Gnome-Shell via the usual `sudo apt-get install gnome-shell`.

After I rebooted, I saw the normal Dell boot screen, but afterwards all I get is a completely black screen.

I can still SSH into the machine and I don't see anything weird in `cat /var/log/syslog | less`, but then again I'm not sure what I'd be looking for.

How do I get my display working again on Mythbuntu and Gnome-Shell?

---

### Post by Cerin on 2013-01-24
In my /var/log/dmesg, I see things like:

[    8.480907] HDMI: detected monitor SAMSUNG at connection type HDMI

and:

[    8.625670] type=1400 audit(1359080873.397:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=888 comm="apparmor_parser"

so it can see the monitor and the lightdm service is running.

---

