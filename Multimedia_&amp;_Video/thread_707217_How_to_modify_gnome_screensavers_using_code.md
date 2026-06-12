---
title: "How to modify gnome screensavers using code?"
date: 2008-02-25
forum: Multimedia &amp; Video
---

### Post by wandalalakers on 2008-02-25
I don't want to install xscreensavers.  Instead I want to do something like this:

(I found this thread)
[http://ubuntuforums.org/showthread.php?t=198809&page=3](http://ubuntuforums.org/showthread.php?t=198809&page=3)

My question is how can I find out what each code exec means?
Ex. On Euphoria, I like the "regular" setting versus "grid" or "cubism".
I also want to be able to change modify the Skyrocket screensaver.
Is this possible without using xscreensaver?  Thx

Euphoria screensaver

Code:
man euphoriaI was able to determine the switches I needed to make Euphoria run as I liked so I then opened the Euphoria file with:


Code:
sudo gedit /usr/share/applications/screensavers/EuphoriaAfter using 'man euphoria' I knew that changing the following line:


Code:
Exec=euphoria -rto:


Code:
Exec=euphoria -r -p 1

---

