---
title: "No Control in Flash"
date: 2010-06-13
forum: Multimedia Software
---

### Post by Intel91 on 2010-06-13
Hey, I have no control over flash on 10.04, and have never had control of flash regardless of which ubuntu or adobe flash/gnuflash I was trying. I can view flash, watch flash, but I can't pause or interact with it in any way. However, oddly enough, if I right click to bring up the options menu, and then I click on something, it works. Does anyone have any idea what is going on, has anyone encountered this?

---

### Post by lovinglinux on 2010-06-13
The problem you are experiencing is common and usually happens when you have a 64bit browser and are using a 32bit plugin. Unfortunately, Adobe recently dropped support for 64bit flash and all available versions have a critical vulnerability (should not be used). I remember seeing a fix somewhere that doesn't involve installing the 64bit plugin, but I can't find it right now. I guess you will need to use that workaround for now.

Anyway, install [FLASH-AID](http://flash-aid-extension.blogspot.com) extension for Firefox. It will remove conflicting plugins and install the proper flash version according to your browser architecture. 

If you don't use Firefox or prefer to fix the problem from command-line, then see the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by lovinglinux on 2010-06-13
Try this:

```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
```

Add the following line before the last line:

```
export GDK_NATIVE_WINDOWS=1
```

Save and restart the browser.

---

### Post by moon911 on 2010-06-20
Thank you very much for your helpful advice. Flash control worked again.

---

