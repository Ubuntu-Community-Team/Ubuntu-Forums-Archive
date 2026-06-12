---
title: "No Flash on my Gutsy"
date: 2008-02-03
forum: Multimedia &amp; Video
---

### Post by HuBaghdadi on 2008-02-03
Hi.
I have Flash player (Adobe Flash)  installed on my Ubuntu 7.10 via Synaptic.
When I tried to display a page that contains Flash object, Firefox complained about it and prompted me to install the missing plugin.
Well, Firefox did a search and told me that I have Flash player installed in my system.
Any ideas?
Thanks.

---

### Post by gandaran on 2008-02-03
the easy way to install flash is go to a web page like youtube, when you get that message flash plugin missing you just click install, your troubles are over, but to do that, first you must remove/deactivate the ubufox addon extension (look it up on firefox menu bar»tools»extras/addons) and restart firefox, you can activate it later if you wish,
uninstall any flash, like flashplugin-nonfree or gnash if you tried doe's first.

the ubufox extension will redirect you to install the flashplugin-nonfree 9.0.48, adobe flash is updated now to version 9.0.115 so the link is broken, (all you get installed is an empty /usr/lib/flashplugin-nonfree folder).
if you use the method above, firefox will install directly from the adobe flash site.

gandaran

---

### Post by HuBaghdadi on 2008-02-06
I found that Adobe Flash plugin installed via Synaptic isn't working.
Installing it by hand works, just get it from Adobe website and run it...

---

### Post by kdog_1914 on 2008-02-06
You can also copy 'libflashplayer.so' from /usr/lib/flashplugin-nonfree to /usr/lib/firefox/plugins

You will also find this file in the tar download on the adobe site.

This was the easiest workaround, although when firefox updates, you'll have to move the plugin (if the package installer has not been fixed by then.)

---

