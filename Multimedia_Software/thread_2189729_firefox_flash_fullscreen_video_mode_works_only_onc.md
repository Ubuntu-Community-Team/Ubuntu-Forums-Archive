---
title: "firefox flash fullscreen video mode works only once, then requires restart"
date: 2013-11-23
forum: Multimedia Software
---

### Post by sascha-baumeister on 2013-11-23
dear forum,

on Ubuntu Gnome 13.10, watching fullscreen flash videos in firefox or chromium works nicely the first time on various sites, like [http://www.thedailyshow.com/full-episodes/](http://www.thedailyshow.com/full-episodes/). However, when i switch back and then try to go back to fullscreen it will no longer work; the video basically freezes until i move the browser window to unfreeze it. This condition can only be reset by restarting the browser, which allows me to go fullscreen a single time once more before the next restart. Note that youtube is an exception to this, fullscreen always works there. As the problem affects video playback in multiple browsers over multiple sites, I suspect something connected to the shared flash plugin.

The problem was already present in Ubuntu Gnome 13.04, but not in Ubuntu 12.10 Gnome Edition (I just checked with an older installation). The problem seems to have been reported before, but the thread was closed without action because it was posted in the wrong forum at the time (Ubuntu +1):
[http://ubuntuforums.org/showthread.php?t=2173647](http://ubuntuforums.org/showthread.php?t=2173647)

In said thread there is a more specific problem description that might help; I see the same behavior regarding ALT-TAB:
"just to make clear, this is what happens: i go to a site with flash  player videos. i click on fullscreen. it works. i go back to normal  view. i click on fullscreen again - it does not work. the video in the  small video area freezes and if i click ALT-TAB i see that there is a  plugin-container 'ghost window' that is basically not working.."

any hints/comments? The behavior is really annoying, and has been so for quite a while now ...

---

### Post by woopah on 2013-11-24
Hi,

I had the same problem and came across your post looking for a solution. I'm on Debian tho, but this worked for me! :

[http://askubuntu.com/questions/305417/adobe-flash-plugin-no-full-screen](http://askubuntu.com/questions/305417/adobe-flash-plugin-no-full-screen)

---

### Post by sascha-baumeister on 2013-11-25
Hi,

thanks for the link, the workaround works for me on Ubuntu Gnome too! :)

---

### Post by alvarolinares on 2014-05-01
Easier solution here: [http://askubuntu.com/a/13247](http://askubuntu.com/a/13247)

> sudo mkdir /etc/adobe
echo "OverrideGPUValidation = 1" | sudo tee -a /etc/adobe/mms.cfg

---

