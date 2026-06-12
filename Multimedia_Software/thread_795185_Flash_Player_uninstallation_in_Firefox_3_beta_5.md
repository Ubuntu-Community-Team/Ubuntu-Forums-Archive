---
title: "Flash Player uninstallation in Firefox 3 beta 5"
date: 2008-05-15
forum: Multimedia Software
---

### Post by svigeneris on 2008-05-15
Hi, first post here.

I've just upgraded from WinXP to 8.04, and it's going well. It comes with Fx3b5, and I'm having trouble with the flash player.

In the plugins dialog it's listed as Flash 9.100, and it's giving me choppy videos on sites like youtube etc.

Now, I downloaded the latest flash 9 version (112, I think), but even though I followed the uninstallation procedure, 9.100 was still on the list. I tried disabling it, but then the video wouldn't show up on the site.

Since then, I've installed the new Flash 10 beta, but it doesn't seem to superimpose over 9.100.

I need some help uninstalling flash, and getting firefox up and running to play videos again.

If you need more info, just let me know. Still new at this, so you may need to walk me through it.

Thanks

---

### Post by plun on 2008-05-15
Welcome  :)


Start the terminal and copy/paste this command


- Firefox not running  !!

```
sudo apt-get purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla  
```


- Install Flash 10


- I can still notice high CPU without **[Adblock Plus]("https://addons.mozilla.org/en-US/firefox/addon/1865")** running

Testcase > 1 tab with YouTube and other tabs with ads messedup sites


- No random crashes with Flash 10


Perhaps also take a look at this sticky thread, a masterpiece...

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

:)

---

### Post by svigeneris on 2008-05-15
Brilliant.

Thanks very much for your help. This thread's a bit more updated than the sticky, which results in reinstallation of flash 9. To be fair, 10's still in Beta, but my videos are working anyway.

Again, thanks.

---

