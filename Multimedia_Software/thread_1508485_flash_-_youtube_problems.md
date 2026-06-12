---
title: "flash - youtube problems"
date: 2010-06-13
forum: Multimedia Software
---

### Post by evan54 on 2010-06-13
The problem:

-Pause button doesn't work on youtube
-Sometimes if I close one of the tabs the video that was playing in a different tab crashes/stops playing and I have to reload the particular tab in order to get it going again.

Remarks:
-This was also an issue under karmic
-When I upgraded to LTS it worked fine and then I installed/uninstalled flash (don't ask me why.... BIG MISTAKE) and since then it isn't working...

I've been reading all kinds of "fixes" but nothing has worked so far... Things like reinstalling flash etc...

any ideas?

---

### Post by lovinglinux on 2010-06-13
The problem you are experiencing is common and usually happens when you have a 64bit browser and are using a 32bit plugin. Unfortunately, Adobe recently dropped support for 64bit flash and all available versions have a critical vulnerability (should not be used). I remember seeing a fix somewhere that doesn't involve installing the 64bit plugin, but I can't find it right now. You might try to right-click on the flash video to bring the options dialog and close it. After that you should be able to click the controls. Is not a solution, just a workaround for now.

Anyway, install [FLASH-AID](http://flash-aid-extension.blogspot.com) extension for Firefox. It will remove conflicting plugins and install the proper flash version according to your browser architecture. 

If you don't use Firefox or prefer to fix the problem from command-line, then see the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by evan54 on 2010-06-13
hm.... hasn't made much of a difference.

First I installed flash-aid from tools->add ons-->get add-ons

Then tried the command line approach, with flash-aid installed.

Youtube commands work only sporadically and not at all consistently...

---

### Post by lovinglinux on 2010-06-13
> **evan54 said:**
> hm.... hasn't made much of a difference.

First I installed flash-aid from tools->add ons-->get add-ons

Then tried the command line approach, with flash-aid installed.

Youtube commands work only sporadically and not at all consistently...

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

### Post by evan54 on 2010-06-13
perfect working!!!

thank youuuuu

---

### Post by cprofitt on 2010-08-18
Great bit of information.

---

