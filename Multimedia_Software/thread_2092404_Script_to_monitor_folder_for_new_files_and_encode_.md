---
title: "Script to monitor folder for new files and encode new ones"
date: 2012-12-07
forum: Multimedia Software
---

### Post by Pixel on 2012-12-07
I'm in the process of creating a server that will monitor new files from dropbox, and when it detects a new file, to encode it to mp4 and save it into another folder on dropbox.

I'll be using HandbrakeCLI for the encoding, and I figured cron + a bash script could do this, but I'm not entirely sure where to begin.

Are there any applications out there that already do something similar to this?

Thanks for any help.

---

### Post by Cheesehead on 2012-12-07
The kernel's inotify service will tell you when a new file is added to a directory.

Many applications and services use inotify. Try the command [FONT="Courier New"]apt-cache search inotify[/FONT] for a list of notification applications.

For example, the incron or inotincoming applications may provide the service you're looking for. So may several others.

---

