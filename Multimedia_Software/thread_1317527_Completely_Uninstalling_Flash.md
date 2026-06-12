---
title: "Completely Uninstalling Flash"
date: 2009-11-06
forum: Multimedia Software
---

### Post by Cerin on 2009-11-06
How do you uninstall Adobe Flash player from Firefox? When I first hit a page requiring Flash, and nice clean dialog popped up asking me if I wanted to install Adobe Flash, Gnash, or SWFDec. I choose Adobe Flash, and found it doesn't work in 64-bit Ubuntu 9.10, so I'd like to try the other players.

However, I can find to way to re-trigger the dialog and Firefox seems to have installed Flash in some mysterious place, so I can't manually remove it. Deleting ~/.mozilla, ~/.macromedia, and uninstalling the "Flash Installer" package has not removed Flash from Firefox. Please help!

---

### Post by wojox on 2009-11-06
Open a terminal and try:

```
sudo apt-get --purge remove flashplugin-nonfree
```

[Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567")

---

### Post by HappyFeet on 2009-11-06
If you want flash to work right, try the [64bit flash]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz") file. Just unzip it and put the libflashplayer.so file into /usr/lib64/mozilla/plugins. Restart firefox.

---

### Post by Cerin on 2009-11-06
@wojox

Thanks, this was actually the first thing I tried, but was surprised to find that flashplugin-nonfree had not yet been installed, which makes me wonder where Firefox got its plugin from.

However, out of curiosity, I tried installing flashplugin-nonfree, and found that it works perfectly. I guess the moral is stay way from Firefox's Flash plugin dialog, and just install it yourself through Synaptic.

---

