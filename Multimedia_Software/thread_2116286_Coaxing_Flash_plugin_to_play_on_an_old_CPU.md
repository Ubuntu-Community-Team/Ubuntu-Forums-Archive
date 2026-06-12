---
title: "Coaxing Flash plugin to play on an old CPU"
date: 2013-02-15
forum: Multimedia Software
---

### Post by heliboy on 2013-02-15
In case this observation is useful to the next gal or guy …
 

 Just completed a new installation of 12.04 on an old home-brewed desktop computer sporting an AMD Duron CPU.  Package flashplugin-installer installed version 11.2.202.270 of libflashplayer.so from Adobe in /usr/lib/mozilla/plugins/.  Nothing Flash would play in Firefox or Chrome.  In Chrome's chrome://plugins, pepperflash did not appear.  Bummer.   
 

 Much googling later, it appears that neither pepperflash nor the current version of Adobe's plugin will work with older CPU's such as my Duron that do not have SSE2 support ([http://code.google.com/p/chromium/issues/detail?id=144680](http://code.google.com/p/chromium/issues/detail?id=144680); [http://en.wikipedia.org/wiki/SSE2](http://en.wikipedia.org/wiki/SSE2)).  The solution is to downgrade Flash, detailed procedures for which are readily available.  In my case, I have a laptop hanging around which has a downgraded version of Flash, and I copied its libflashplayer.so (11.1r102) into the desktop's /usr/lib/mozilla/plugins/ after purging flashplugin-installer.  The desktop now plays Flash fine through both Firefox and Chrome.   
 

 I'm not very knowledgeable about these things, so a better way to address this problem probably exists.  In particular, security risks may be involved.  But my old CPU is now playing things Flash.

---

