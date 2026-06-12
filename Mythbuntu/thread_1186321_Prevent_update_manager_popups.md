---
title: "Prevent update manager popups"
date: 2009-06-13
forum: Mythbuntu
---

### Post by bcg30506 on 2009-06-13
Is there anyway to stop the graphical update-manager in mythbuntu 9.04 from automatically running and popping up notification windows over mythfrontend?  This greatly reduces the WAF as the only way to get rid of it is to VNC in and click Close.  I check for updates when I ssh in and upgrade with apt-get so I do not need the graphical notifiers on my living room system.  Once mythfrontend loses focus the remote control is useless.  Plus it introduces risk if she accidentally said upgrade trying to get rid of the window.  I don't want each weekly change to automatically run to keep the box stable and working for everyone on our TV.

---

### Post by Neon Dusk on 2009-06-13
You can return to the old notifications using 
```

gconftool -s --type bool /apps/update-notifier/auto_launch false

```

---

### Post by bcg30506 on 2009-06-13
Sorry, maybe I'm being dense.  What do you mean by "return to the old notifications?"  I don't want any GUI update-manager to run.  I only want to see the motd for updates when I ssh in and do upgrades with apt-get instead of the GUI since I don't have a mouse or keyboard on this box.

---

### Post by lightpower on 2009-06-14
Under Administration -> software manager there is an option to control the way updates are handled. I missed it now. Will check on my machine and will update

---

### Post by Neon Dusk on 2009-06-14
> **bcg30506 said:**
> Sorry, maybe I'm being dense.  What do you mean by "return to the old notifications?"  I don't want any GUI update-manager to run.  I only want to see the motd for updates when I ssh in and do upgrades with apt-get instead of the GUI since I don't have a mouse or keyboard on this box.

The update notification changed in 9.04 - in previous versions an icon appeared in the notification area letting you know how many updates were available (which doesn't interfere with mythtv).

See [here](http://www.ubuntumini.com/2009/05/remove-pop-up-update-manager.html) for screen shots.

---

### Post by bcg30506 on 2009-06-15
Thanks to all of you.  I've run the command:

gconftool -s --type bool /apps/update-notifier/auto_launch false

and now we'll wait and see if that takes care of it the next time updates are available.

---

