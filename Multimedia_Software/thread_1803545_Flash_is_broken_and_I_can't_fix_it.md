---
title: "Flash is broken and I can't fix it"
date: 2011-07-13
forum: Multimedia Software
---

### Post by Hakaron on 2011-07-13
Hi everybody,

I have been having some problems with Flash in Firefox and after scouring the net on how to improve flash performance, I've somehow (really wish I knew how exactly) managed to break it entirely. I have since tried installing the x64 variant, tried purging everything, removing and re-installing Firefox, installing chromium, but nothing seems to work...

Would there be any way to completely remove Firefox and any of its' settings that seem to roam around or must I resort to fixing Kubuntu 11.04 the same way I always end up "fixing" Windows: Just pop the installation cd into the drive and perform a clean install... I'm still backtracing my steps here a little, so I'll update as I get less grumpy and frustrated at this...:(

P.S. Feel free to move this thread should I have posted in the wrong section...

EDIT: downloading 32-bit flash from adobe and using nspluginwrapper as recommended on [http://plugindoc.mozdev.org/linux-amd64.html#flash-npwrap](http://plugindoc.mozdev.org/linux-amd64.html#flash-npwrap) seems to have partially fixed it__[URL="http://http//plugindoc.mozdev.org/linux-amd64.html#flash-npwrap"]
[/URL]

---

### Post by Hakaron on 2011-07-13
Ok, I think the problem really started to spiral out of control when I copy/pasted the following from [this]("https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins") into my terminal(Konsole, I used the middle mouse button if that makes any difference):

```

sudo apt-get purge flashplugin-nonfree flashplugin-installer gnash gnash-common mozilla-plugin-gnash swfdec-mozilla
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/flashplugin-alternative.so
sudo rm -f /usr/lib/mozilla/plugins/npwrapper*flash*so
rm -f ~/.mozilla/plugins/*flash*so

```After that Firefox seems to be extremely sluggish (kinda like it is on Windows) and flash was no longer operational...

Sorry for sending this in so late, but dinner was ready after my initial post...

---

