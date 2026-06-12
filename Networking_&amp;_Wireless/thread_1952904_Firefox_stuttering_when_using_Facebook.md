---
title: "Firefox stuttering when using Facebook"
date: 2012-04-05
forum: Networking &amp; Wireless
---

### Post by joschak on 2012-04-05
Hi everyone,

after a few months of Linux-abstinency I just reinstalled Kubuntu (11.10 x86-64) on my desktop PC yesterday. Apart from some smaller inconveniences, everything seems to work fine except for Firefox: When I'm using Facebook, Firefox stutters all the time and freezes every thirty seconds when I click a link, load a photo etc. I tried to deactivate all plug-ins but the problem was the same. The problem did not occur when I was using Firefox on my Windows system on the same PC.

I then tried rekonq where the same problem occured, although it worked slightly better. However, today I installed Opera and with that everything works fine, so the problem must be caused by the browser and not by the system. As I don't really fancy Opera, though, and I'd like to continue using Firefox, I wanted to ask if anyone here has had the same problem or has any idea about how to fix it?


Joscha

PS: At the moment, Facebook is the only website Firefox seems to be troubled with, so I guess the problem is about the whole lot of AJAX there. If anybody knows another web page using a lot of AJAX I might check out that one as well to see if the same problem occurs.

---

### Post by lovinglinux on 2012-04-05
Facebook always cause such problems. It seems they use a lot of javascript and are constantly messing things.

Install [NoScript](https://addons.mozilla.org/en-US/firefox/addon/noscript/) and block the scripts. I don't use Facebook, so I don't know which services would be affected by blocking scripts, but another user was experiencing high CPU usage on Facebook an NoScript did the trick.

---

