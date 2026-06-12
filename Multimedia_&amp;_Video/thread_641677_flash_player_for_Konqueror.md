---
title: "flash player for Konqueror"
date: 2007-12-15
forum: Multimedia &amp; Video
---

### Post by fitlad on 2007-12-15
Hi there,
I'm currently running kubuntu feisty fawn and I'm trying to install adobe flash player plugin then configure it with konqueror. According to this thread [http://ubuntuforums.org/showthread.php?t=636397&highlight=konqueror+flash]("http://ubuntuforums.org/showthread.php?t=636397&highlight=konqueror+flash"), "The new version of Flash is incompatible with Konqueror because it requires XEmbed (Launchpad Bug# 174343). 9.0.48.0 is the last version of flash to support Konqueror in its current state". Thus, I downloaded the recommended version in source package format and I tried to install it through konsole.
[PHP]$ sudo -i
 # tar zxvf install_flash_player_9r48_linux.tar.gz
 # cd install_flash_player_9_linux/
 # ./flashplayer-installer
 # exit [/PHP]
The biggest problem that I faced during the installion was to identify the install location of konqueror; I searched /usr/lib/ for the required folder but I found none. I even tried to create a folder merely to install the flash player plugin but it didn't work that way :confused: The installation wizard kept requesting a valid "install location". I honestly don't know what to do???:confused: I still prefer to configure konqueror rather than dump it in favour of firefox. Any suggestion and suppot is appreciated. Thanks.

---

### Post by neptho on 2008-02-02
Just copy flashplayer.xpt and libflashplayer.so to /usr/lib/flashplugin-nonfree, and rescan your plugins.

```
sudo cp flashplayer.xpt /usr/lib/flashplugin-nonfree
sudo cp  libflashplayer.so /usr/lib/flashplugin-nonfree
```

Open Konq, go to Tools, Settings, Plugins, Scan for New Plugins.

---

