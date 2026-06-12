---
title: "System hang, any way to debug ?"
date: 2008-07-18
forum: Mythbuntu
---

### Post by erland on 2008-07-18
My Mythbuntu box totally hanged two days ago, it was totally locked and didn't accept any mouse movements or keyboard commands. The main menu in MythTV was still shown so it was still able to produce a picture to the graphics card. It was no longer available on the network after the hang, so it was not possible to access it in any way. The only way to get it back was to do a hard reset using the power buttons.

When it started up again it did fsck and then continued to work as usual.

After I got it up I tried to look in the logs, such as:
- /var/log/syslog
- /var/log/mythtv/mythbackend.log
- /var/log/messages
- /var/log/kern.log

In all the log files it just seemed like it had stopped without logging anything special, no error message or nothing strange as far as I could see.

Is there any other log files I should look at to get some knowledge regarding what could have caused the crash ?

Is the power button the only way to get out of a situation like this when it has totally hanged, or is there some better way ?

---

### Post by laga on 2008-07-18
> Is there any other log files I should look at to get some knowledge regarding what could have caused the crash ?

Um. Sasc-ng maybe? ;)

---

