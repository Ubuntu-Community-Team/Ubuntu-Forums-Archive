---
title: "Flash - Not performing as expected."
date: 2010-01-15
forum: Multimedia Software
---

### Post by tagger on 2010-01-15
The recommended flash players for ubuntu 8.04 do not make proper use of the "wmode" attribute and cause problems for websites that use dynamic menu's and flash animation.  (css/javascript)

I tested the nonfree, sfwdec, and gnash flash players from the ubuntu repositories. They all exhibit this problem.  Installing the .deb from Adobe eliminated this problem.

I tested in quite a few browsers.
Firefox 3.0.17, Sea Monkey 1.1.17, SeaMonkey 2.0.2, Google Chrome, Opera 10.10.

I tested the same browsers in Windows and Mac platforms to ensure that the web pages were coded properly. They only gave a problems on Ubuntu.

So... if you are having a problem with flash appearing on top of things in websites... (like menus) uninstall all of the flash players that show up in synaptic, then Get the latest from Adobe and install it.  

The problem is the wmode property is not being observed as expected in the other flash players and they are playing on top of everything else in the site.

Hope this helps someone.

---

### Post by Dennis N on 2010-01-15
You are right. The flashplugin-nonfree package in the main Hardy repos is actually still version 9 it seems. 

version: 10.0.1.218+really9.0.260.0ubuntu1

Looks like ver 10, but note the last part. Firefox 3.0.17 identifies it as Shockwave Flash ver 9 r 260, and so does Adobe's version test page. 

You can also get a true version 10 for Hardy by enabling the Canonical 'Ubuntu Hardy Partner' repository which is found under Third Party Software tab in the Software Sources. This provides the same package (adobe-flashplugin) that is offered on the Adobe web site, I believe. With the repo enabled you should get automatic updates as well.

---

