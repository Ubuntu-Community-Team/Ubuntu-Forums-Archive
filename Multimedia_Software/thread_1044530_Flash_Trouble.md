---
title: "Flash Trouble"
date: 2009-01-19
forum: Multimedia Software
---

### Post by The Last Of The Brunnen-G on 2009-01-19
I'm having Flash trouble. I'm using 7.10.

I recall having installed Flash by responding to the Firefox pop-up when I went to a web-page that had Flash content, but didn't yet have Flash installed. Right now, when I look in my Firefox Add-ons list, "Shockwave Flash 9.0 r999" is on the list.

When I go to a page with Flash content, such as a Youtube page, the content loads, but when I hit play, the video is garbled and the audio skips. It's not right.

I can "disable" the Add-on from within Firefox, but I don't see a way to actually remove it completely.

I tried installing flashplugin-nonfree with apt-get. When I do it says that it has successfully installed Flash 10, but when I go back to Firefox, the same old buggy Flash 9 is all that's there, and Flash still doesn't work right.

I have a hunch that the key to all of this will be uninstalling the buggy add-on. How can I do that?

---

### Post by gandaran on 2009-01-19
the  flashplugin-nonfree package in ubuntu 7.10 is no longer maintained, so you don't have this adobe flash installed much less flash 10, what most likely you have installed is gnash or swfdec flash plugin, I recommend you use synaptic package manager to remove completely all flash plugins be it gnash, swfdec, libflash and the flashplugin-nonfree.
the only way to install adobe flash in ubuntu 7.10 now is to get the .tar.gz package here [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
to install either run the installer or unpack/extract the package and just drag or drop the libflashplayer.so file to /home/'user'/.mozilla/plugins (make the plugins folder) or /usr/lib/mozilla/plugins

---

### Post by wolfen69 on 2009-01-19
i suggest using ubntu 8.04 (fresh install) and doing ```
sudo apt-get install ubuntu-restricted-extras
``` flash should work then.

---

### Post by The Last Of The Brunnen-G on 2009-01-20
> **gandaran said:**
> the  flashplugin-nonfree package in ubuntu 7.10 is no longer maintained, so you don't have this adobe flash installed much less flash 10, what most likely you have installed is gnash or swfdec flash plugin, I recommend you use synaptic package manager to remove completely all flash plugins be it gnash, swfdec, libflash and the flashplugin-nonfree.
the only way to install adobe flash in ubuntu 7.10 now is to get the .tar.gz package here [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
to install either run the installer or unpack/extract the package and just drag or drop the libflashplayer.so file to /home/'user'/.mozilla/plugins (make the plugins folder) or /usr/lib/mozilla/plugins

That worked. Thanks!

---

### Post by The Last Of The Brunnen-G on 2009-01-20
> **wolfen69 said:**
> i suggest using ubntu 8.04 (fresh install) and doing ```
sudo apt-get install ubuntu-restricted-extras
``` flash should work then.

I'm not reinstalling my entire operating system to get flash working.

---

