---
title: "choppy flash, trouble reinstalling"
date: 2009-06-26
forum: Multimedia Software
---

### Post by hotweld79 on 2009-06-26
I've just loaded up Ubuntu 8.10 on a clean hard drive.  I installed Adobe's flash player, but it ran too choppy.  I followed the directions on another post to uninstall using this command line:

 sudo apt-get install flashplugin-nonfree --purge

Then it download and installed *another* flash program.  How can I get this off my computer and try again?

---

### Post by lovinglinux on 2009-06-26
The solution to your problem is in the Troubleshooting section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

> **lovinglinux said:**
> 
Some video issues are caused by conflicting plug-ins. It's not a good idea to have multiple plug-ins for the same type of content.

To remove conflicting flash plug-ins and install only the one from Adobe open "Applications >> Accessories >> Terminal", then paste (CTRL+SHIFT+V) the code below in the terminal window and hit enter:

```
sudo apt-get remove swfdec-mozilla mozilla-plugin-gnash && sudo apt-get install flashplugin-nonfree 
```



---

