---
title: "Use Google Chrome Flash Plugin in Firefox!"
date: 2011-01-07
forum: Multimedia Software
---

### Post by JosephPaul on 2011-01-07
I have devoted several threads to my effort to improve my flash player performance in Firefox in Ubuntu.  I found the following information on this website: [http://www.omgubuntu.co.uk/2010/11/use-chromes-auto-updated-flash-in-firefox/](http://www.omgubuntu.co.uk/2010/11/use-chromes-auto-updated-flash-in-firefox/)

This works like a charm.  I got flash performance as good as Google Chrome with Compiz running and everything.  It is a shame this has to be done to sort out my flash problems, but it has resolved all my issues with flash in Ubuntu.

[LIST]
[*]Open a Terminal session and navigate to the following directory: -
[LIST]
[*]**cd /usr/lib/firefox-addons/plugins**
[/LIST]
 
[*]Now link the Flash player from Chrome to Firefox by running this command: -
[LIST]
[*]**sudo ln -s /opt/google/chrome/libgcflashplayer.so ./**
[/LIST]
 
[/LIST]
 Now open Firefox, head to the ‘Add-ons > Plugins’ menu and disable the default version of Flash (if any).

---

### Post by lovinglinux on 2011-01-07
You could also use my [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/161939/") extension, to keep flash updated with the beta releases and automatically apply performance tweaks.

---

### Post by lovinglinux on 2011-01-07
BTW, keep in mind that only Chrome 32bit is shipped with the plugin, so don't try this on 64bit system, because the file doesn't exist.

---

### Post by lovinglinux on 2011-01-07
I have tested this on firefox 4.0b9pre and 3.6.13 on Lucid and it only works if you remove the current flashplugin from the repositories and use this instead:

```
sudo ln -s /opt/google/chrome/libgcflashplayer.so /usr/lib/mozilla/plugins/libflashplayer.so
```

I'm implementing this option in my extension for the next version, however, I still recommend the beta from Adobe.

---

### Post by lovinglinux on 2011-01-07
Released [Flash-Aid version 2.0.2]("http://www.webgapps.org/addons/flash-aid") with such functionality.

---

