---
title: "Adobe Flash Player 11 on Ubuntu x86-64"
date: 2011-08-15
forum: Multimedia Software
---

### Post by slayer^_^ on 2011-08-15
Ok, with the recent release of the native version of 64 bit flash player for Linux (and Ubuntu Linux), this post may seem obsolete... I'm just keeping some useful info !



1) Experiencing troubles ? Be sure to **remove previous existing versions of flash player**: type in terminal, string by string:

```

sudo apt-get remove --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash 
sudo apt-get remove --purge swfdec-mozilla libflashsupport nspluginwrapper iceape-flashplugin 
sudo apt-get remove --purge iceweasel-flashplugin mozilla-flashplugin firefox-flashplugin 
sudo apt-get remove --purge xulrunner-flashplugin midbrowser-flashplugin xulrunner-addons-flashplugin
sudo rm -f /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
sudo rm -f /usr/lib/iceweasel/plugins/npwrapper.libflashplayer.so
sudo rm -f /usr/lib/firefox/plugins/npwrapper.libflashplayer.so
sudo rm -f /var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so
sudo rm -f ~/.mozilla/plugins/npwrapper.libflashplayer.so
sudo rm -f /usr/lib/firefox-addons/plugins/npwrapper.libflashplayer.so
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -f /usr/lib/mozilla/plugins/*flash*

```

2) Install the package, present in the ubuntu repositories:

```

sudo apt-get install adobe-flashplugin

```

or install the adobe-flashplugin package via synaptic package manager or Ubuntu software center.

That's all folks !

Just, in the end, a thought for Steve Jobs who recently passed away. R.I.P.

---

### Post by lovinglinux on 2011-08-15
...or just get [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/") and run it's wizard.

---

### Post by Gillo_ on 2011-08-15
Thank you, Slayer^_^!! This worked like a charm, I can finally watch videos on youtube thanks to you!

---

### Post by michael37 on 2011-10-06
This version of flash is no longer valid. Upgrade to the latest released version.

[thread=1358591]Instructions here[/thread]

---

