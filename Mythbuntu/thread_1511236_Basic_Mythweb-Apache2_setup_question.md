---
title: "Basic Mythweb-Apache2 setup question"
date: 2010-06-16
forum: Mythbuntu
---

### Post by tmcgary on 2010-06-16
After reading some threads it seems that securing mythweb as detailed here [http://www.mythtv.org/wiki/MythWeb#Apache_Configuration](http://www.mythtv.org/wiki/MythWeb#Apache_Configuration) is more secure than just using the Mythbuntu Control Centre. However, is it necessary to enable the settings in MCC first before editing Apache via the console? Thanks!

---

### Post by newlinux on 2010-06-16
No it is not necessary. Not sure what will happen if you make the edits and then go use the configuration in MCC (will it overwrite?).

Just taking a quick glance at that page, I'm not sure how that is much more secure than what MCC implements and those instructions don't look to be exact for how things are in ubuntu. 

For example, Directory "/var/www/html/mythweb" is not right for ubuntu (I believe it is /var/www/mythweb).

---

### Post by tmcgary on 2010-06-16
Thanks for the headsup. Maybe I'll start off with the MCC then. I am super green with the console so a GUI might be better.

---

