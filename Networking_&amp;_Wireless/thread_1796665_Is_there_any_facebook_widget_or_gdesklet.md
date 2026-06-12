---
title: "Is there any facebook widget or gdesklet???"
date: 2011-07-04
forum: Networking &amp; Wireless
---

### Post by lalitha niharika on 2011-07-04
I want small facebook tab like widget on my desktop.It is available in kubuntu.Is there any way to create it??I should be able to view updates,update my status etc...

---

### Post by sikander3786 on 2011-07-08
You can try using Screenlets.

From Terminal:

```
sudo apt-get install screenlets
```

Don't start it yet. Download the Facebook widget from here:

[http://screenlets.org/index.php/Facebook](http://screenlets.org/index.php/Facebook)

Extract the downloaded package to the hidden .screenlets direcotry in your home directory. You'll need to press Ctrl + H to see the hidden files/directories.

Now start Screenlets by going to Applications > Accessories > Screenlets in Gnome or by searching the Dash in Unity.

Look for 'Facebook' and select it. In the left column, enable 'Start/Stop' and 'Auto start on login'. You'll need to login to Facebook using your Web Browser.

If something doesn't work straightaway, re-login or a reboot might help.

Good Luck!

---

