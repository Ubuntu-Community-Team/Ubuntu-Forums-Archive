---
title: "nm-applet disappeared from the panel"
date: 2011-03-30
forum: Networking &amp; Wireless
---

### Post by robro on 2011-03-30
Hello community,
the nm-applet seems to have disappeared from the top panel, whenever I run the command it gives me the output:

```

** Message: applet now removed from the notification area
** (nm-applet:8695): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:8695): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:8695): DEBUG: old state indicates that this was not a disconnect 0
** Message: applet now embedded in the notification area

```I have tried the --sm-disable parameter but that doesn't help ether :(

Thanks for the help.

---

### Post by dineshs on 2011-03-30
Did you try 
Right click on the top panel-click add to panel-select notification area -click add

---

### Post by robro on 2011-03-30
yep thats the first thing I tried.

---

### Post by dineshs on 2011-03-30
If /etc/network/interfaces contain anything other than```
auto lo
iface lo inet loopback
```
the icon may disappear
See step-1 in
[http://ubuntuforums.org/showpost.php?p=9611450&postcount=2](http://ubuntuforums.org/showpost.php?p=9611450&postcount=2) 
and restart

---

