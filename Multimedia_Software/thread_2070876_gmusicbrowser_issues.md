---
title: "gmusicbrowser issues"
date: 2012-10-13
forum: Multimedia Software
---

### Post by MoralAnarchy on 2012-10-13
Hey guys! Linuxnoob using Ubuntu 12.04.1 LTS.  I am having trouble with my gmusicbrowser.  I want to keep a certain kind of layout of my gmb on my desktop.  I am using VastOne's plugins for his desktop widgets and using the lyrics widget with the plug in.  It's all working great except that when I close my gmb session and reopen the only thing that pops up is the generic mini player which is annoying because all the settings for my preferred widget are still in the plug ins section of the settings page but i have to go in and select then deselect the on top of other windows option for it to show up again on my desktop.  I am wondering if there is a way for me to make it so when I launch gmb those desktop settings will show up.  Sorry if this explanation sucks but I'm going off of memory as I'm at work right now.  If any of you can help me and need any additional informatin/certain of my scripts etc then let me know and I will post as soon as I get out of this prison!!!! haha.  Thanks guys.  cheers.

---

### Post by pqwoerituytrueiwoq on 2012-10-13
when you logout it crashes (or terminates) gmb
you need to close it gracefully before logout
*will edit with fix, i have it on my laptop*
edit:
```
sudo bash -c "echo 'session-cleanup-script=/usr/local/bin/xfce-logout-script'  >> /etc/lightdm/lightdm.conf"
```
and install the attached script to
```
/usr/local/bin/
```
the changes will be applied after lightdm is restarted

---

### Post by MoralAnarchy on 2012-10-13
> **pqwoerituytrueiwoq said:**
> when you logout it crashes (or terminates) gmb
you need to close it gracefully before logout
*will edit with fix, i have it on my laptop*
Forgive me but I don't know what you mean by 'close it gracefully'.  Do you simply mean 'x' out before I log off my current DE or shut down?  If you could please elaborate :)

---

### Post by pqwoerituytrueiwoq on 2012-10-14
close it before logout/shutdown
if you look at my edit it will do that automatically when you logout/shutdown

---

### Post by MoralAnarchy on 2012-10-14
great! thanks mate!  I appreciate it.

---

