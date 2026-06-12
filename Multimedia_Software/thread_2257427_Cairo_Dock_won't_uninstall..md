---
title: "Cairo Dock won't uninstall."
date: 2014-12-19
forum: Multimedia Software
---

### Post by andrew_s4 on 2014-12-19
I'm a newbie to Ubuntu running 14.04. Everything has been running very well without problems, until tonight.
I downloaded the Cairo Dock 3.3.99 beta 1.2 from the Ubuntu Software Center the other day. Not impressed and don't want it and tried to uninstall it via the Ubuntu Software Center. It went through the motions of uninstalling and now gives me the option of installing again. But, it didn't uninstall. So on my computer, under the search function / Applications, when typed in, it is still there and when clicking the icon it will run as normal. So I clicked on the uninstall button there, and nothing happens, it remains. Restarting doesn't refresh or remove the app. Any suggestions as to how I can get rid of it?

---

### Post by andrew_s4 on 2014-12-19
ok I ran this in terminal   sudo apt-get remove --purge cairo-dock* It has now left the stage! I hope nothing else with it...

---

### Post by ajgreeny on 2014-12-19
You can find out what else it took with it by using the command ```
grep -iw remove /var/log/dpkg.log.1 /var/log/dpkg.log
```
It will list everything removed recently line by line with the date and time shown at the start of each line.

---

