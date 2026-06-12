---
title: "[SOLVED] 8.04 Flash starts, but freezes..."
date: 2008-11-16
forum: Multimedia Software
---

### Post by longtex on 2008-11-16
... after 2 seconds. 

Ubuntu 8.04 Firefox 3.0.3 Flash 10 r12

This is identical to an issue I've seen on WinXP boxes - starts, runs 2 seconds, stops. On the XP boxes, disabling the plugin and reenabling makes it work (for some period of time), but not on Ubu...

It also freezes FF sometimes, and there is a hidden, non-responding window labeled npviewer.bin which has to be force-killed.

I am certain that a week ago, youtube was working, but since I updated the flash player, it now quit - and the site that claims to need Flash 10 still doesn't work, either - in case you want to look at it, it's [http://justin.tv](http://justin.tv) and it's a host for straming video. I have been using it to watch broadcast college football games (on the WinXP boxes - if youy get a chance to check it out (lots of other streaming stuff) I'd love to hear some feedback.

Meantime... hell I'd be happy if I could just get youtube working again!

---

### Post by psyke83 on 2008-11-16
You're using an outdated version of nspluginwrapper with Flash. If you visit a site that uses "windowless mode" Flash content, nspluginwrapper will experience a segmentation fault. The solution is to upgrade nspluginwrapper. Also, if you have libflashsupport installed, remove it (it causes crashes as well).

I highly recommend you take a look at my [PulseAudio Fixes]("http://ubuntuforums.org/showthread.php?t=789578") guide. By adding my PPA to your repository lists, you will gain access to updated packages including Flash and nspluginwrapper, and following the guide itself will resolve problems with PulseAudio.

NB. I don't know how you installed Flash 10. If you installed the deb via the adobe site, remove it before following the guide:
```
$ sudo apt-get remove --purge adobe-flashplugin
```
If you installed it manually:
```
$ sudo update libflashsupport
$ locate libflashplayer.so
```

Delete all instances of the "libflashplayer.so" file.

---

### Post by longtex on 2008-11-17
> **psyke83 said:**
> You're using an outdated version of nspluginwrapper with Flash. If you visit a site that uses "windowless mode" Flash content, nspluginwrapper will experience a segmentation fault. The solution is to upgrade nspluginwrapper. Also, if you have libflashsupport installed, remove it (it causes crashes as well).

I highly recommend you take a look at my [PulseAudio Fixes]("http://ubuntuforums.org/showthread.php?t=789578") guide. By adding my PPA to your repository lists, you will gain access to updated packages including Flash and nspluginwrapper, and following the guide itself will resolve problems with PulseAudio.

NB. I don't know how you installed Flash 10. If you installed the deb via the adobe site, remove it before following the guide:
```
$ sudo apt-get remove --purge adobe-flashplugin
```
If you installed it manually:
```
$ sudo update libflashsupport
$ locate libflashplayer.so
```

Delete all instances of the "libflashplayer.so" file.

Thanks for the response! I more-or-less figured this out after plowing through one thread to the bitter end (past all the Flash 9 stuff). I disabled flash, closed FF, manually deleted all files with "flash", libs and all, deleted the wrapper references, reinstalled the whole mess, and rebooted... et voila! Seems to be functioning. I think the problem may have been not so much outdated as wrong arch - my new computer is an amd64 and I think I had i386 stuff installed.

Any road, it seems to be okay - I'll know for sure when I get home this evening, but when I turned in last night, it looked to be good... at least youtube and a couple of other video sites were working, and I think the justin.tv ran okay as well.

Now... if I can just get the mic and line-in to record I can get audacity running and start doing some multi-track recordings with Linux instead of Windoze...

Thanks for the help - I do appreciate it!

---

