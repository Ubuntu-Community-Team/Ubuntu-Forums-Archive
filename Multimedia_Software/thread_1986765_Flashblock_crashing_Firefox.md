---
title: "Flashblock crashing Firefox"
date: 2012-05-25
forum: Multimedia Software
---

### Post by cyberhood on 2012-05-25
Hi ubuntuians,

So the problem I have is that when I click on a YouTube video (or similar site's video) to unlock [Flashblock]("https://addons.mozilla.org/en-US/firefox/addon/flashblock/") to watch a video my entire browser just disappears! A crash without warning or notice! While troubleshooting I found that when I have Flashblock disabled or uninstalled the videos work just fine. I enjoy using Flashblock so any help getting this fixed would be sweet.

thanks :)

---

### Post by ajgreeny on 2012-05-25
Start firefox in terminal with command ```
firefox
``` and see if any errors are reported when flash crashes the browser session.

---

### Post by cyberhood on 2012-05-25
```
~$ firefox
exception in getExpando
no loadgroup notificationCallbacks for http://www.youtube.com/get_video_info?video_id=D6z6hn6wZlg&fmt=18
no loadgroup notificationCallbacks for https://www.youtube.com/get_video_info?video_id=D6z6hn6wZlg&fmt=18
Segmentation fault
```

---

### Post by dentaku65 on 2012-05-25
Check in
```
about:config
```
The entry:
```
dom.ipc.plugins.enabled
```
Unfortunately must be set as *true* (since FF 12 in Ubuntu)

by

---

### Post by cyberhood on 2012-05-25
> **dentaku65 said:**
> Check in
```
about:config
```
The entry:
```
dom.ipc.plugins.enabled
```
Unfortunately must be set as *true* (since FF 12 in Ubuntu)

by
I couldn't find ```
dom.ipc.plugins.enabled
``` in about:config

I'm using Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.1.16) Gecko/20120511 Iceweasel/3.5.16 (like Firefox/3.5.16)

thanks

---

