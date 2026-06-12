---
title: "firefox mplayer plugin won't work"
date: 2007-03-29
forum: Multimedia &amp; Video
---

### Post by Mets on 2007-03-29
I use the mplayer plugin for firefox because we all know totem never works and the VLC plugin is still buggy.  Recently there was a firefox update that was sent out.  I downloaded it and it put totem back as being the default plugin.  If you go to remove the totem plugin it says you have to remove the Ubuntu desktop.  I've tried uninstalling and reinstalling the mplayer plugin but firefox just refuses to use it - it always uses the totem plugin.  Is there a way I can make it use the mplayer plugin by default?

---

### Post by xstaticxgpx on 2007-03-29
personally, what I use is the firefox extension MediaPlayerConnectivity, and it just launches the embedded video in mplayer.

---

### Post by chocbar31 on 2007-03-29
Don't use the built-in package managers to remove the plugins.

Go to your Mozilla plugins' directories and delete all the totem plugins manually, as root. Next time the totem plugins are called, they won't be found and should then resort to the MPlayer plugins.

---

### Post by Mets on 2007-04-01
thanks chocbar!

---

### Post by fearpi on 2007-04-01
> **chocbar31 said:**
> Don't use the built-in package managers to remove the plugins.

Go to your Mozilla plugins' directories and delete all the totem plugins manually, as root. Next time the totem plugins are called, they won't be found and should then resort to the MPlayer plugins.

Where exactly is that directory? I can't find it.

Edit: I found it. For future reference, check /usr/lib/mozilla/plugins and /usr/lib/mozilla-firefox/plugins and /usr/lib/firefox/plugins.

---

### Post by ubu-for on 2007-04-03
> **chocbar31 said:**
> Don't use the built-in package managers to remove the plugins.

Synaptic works great with Feisty now!

Alternatively try [this](http://ubuntuforums.org/showthread.php?t=365239&page=3)!

---

### Post by Mets on 2007-04-05
wow that's actually a lot easier, thanks ubu-for, sweet hack!

---

