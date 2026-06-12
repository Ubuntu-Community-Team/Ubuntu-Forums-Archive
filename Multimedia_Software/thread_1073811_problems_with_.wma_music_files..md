---
title: "problems with .wma music files."
date: 2009-02-18
forum: Multimedia Software
---

### Post by Fons van der Plas on 2009-02-18
Hi,

I have some problems with playing .wma music files. I really installed all codecs possible and after that didn't work, I opened my Exaile Music Player in the terminal. When I tried to open a .wma file I got the following message:

Failed to load plugin
Traceback (most recent call last):
  File "/usr/share/exaile/xl/plugins/manager.py", line 62, in initialize_plugin
    plugin = __import__(re.sub('\.pyc?$', '', file))
  File "/home/fons/.exaile/plugins/alarmclock.py", line 1
     <!--: spam
     ^
 SyntaxError: invalid syntax

Does anyone know what to do?

---

### Post by cariboo on 2009-02-18
It could be there is a drm problem, causing the error you are getting. .wma is a Microsoft standard only.

Jim

---

