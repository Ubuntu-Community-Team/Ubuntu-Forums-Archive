---
title: "Firefox Crashed"
date: 2009-03-24
forum: Networking &amp; Wireless
---

### Post by acmariner99 on 2009-03-24
The last update I installed for firefox caused it to stop working properly. The screen comes up, but the user interface is gone and I cannot use it at all. Would uninstalling and reinstalling firefox be the most prudent solution?

---

### Post by ajgreeny on 2009-03-24
Try renaming the hidden ~/.mozilla folder in your /home as ~/.mozillabak and restart firefox.  If all is now well, it would appear that your configuration for the browser is causing the problem.  The most important part of that will be the bookmarks from the old version, and you will find them as the file ~/.mozilla/firefox/*random*.default/places.sqlite in the old version, so just copy it over to the new folder, but I would not do the same with the other files as one of them may be the cause of the problem in the first place.
PS. The random in italics above is a random alphanumeric which makes up the folder name, it is not actually called random.default.  Sorry if you already knew that, but not everybody does.

---

