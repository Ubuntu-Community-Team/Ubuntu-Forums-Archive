---
title: "Youtube is a black screen (Ubuntu x64 Chromium)"
date: 2011-04-08
forum: Multimedia Software
---

### Post by RobotGymnast on 2011-04-08
I installed a minimal Ubuntu build, and on top of that, Chromium and flashplugin-installer. It used to work fine (with minor glitches), but I recently had an issue where Youtube was a black screen, but other flash worked fine. Reinstalling the plugin solved the issue, but I have the problem again, and it's not helping this time, nor is rebooting. Can anybody help?

---

### Post by Codemagnet on 2011-04-08
Hi, is the same thing happening in Firefox? If not, try reinstalling chrome, might help.

---

### Post by wolfen69 on 2011-04-08
Uninstall flashplugin-installer, and get [64bit]("http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_2_p3_64bit_linux_111710.tar.gz") flash. Put the file in your home folder. Right click it and **extract here**. Open a terminal and:
```
sudo cp libflashplayer.so /usr/lib64/mozilla/plugins
```

Even though it is being copied to mozilla's folder, chromium will pick up on it. Restart chromium. Let us know how it goes.

---

### Post by RobotGymnast on 2011-04-08
> **wolfen69 said:**
> Uninstall flashplugin-installer, and get [64bit]("http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_2_p3_64bit_linux_111710.tar.gz") flash. Put the file in your home folder. Right click it and **extract here**. Open a terminal and:
```
sudo cp libflashplayer.so /usr/lib64/mozilla/plugins
```

Even though it is being copied to mozilla's folder, chromium will pick up on it. Restart chromium. Let us know how it goes.

No change at all - would having nspluginwrapper still installed make any kind of difference?

Update: It started working now. I suspect that copying the 64-bit plugin did work, but for whatever reason, it took a while to do so.

---

### Post by Yellow Pasque on 2011-04-08
Copying files directly into /usr/lib like that is not recommended. I would recommend you remove the file you installed and just use sevenmachines' PPA, as everything is neatly .deb packaged and automatically updated for you. [https://launchpad.net/~sevenmachines/+archive/flash](https://launchpad.net/~sevenmachines/+archive/flash)

> **RobotGymnast said:**
> Update: It started working now. I suspect that copying the 64-bit plugin did work, but for whatever reason, it took a while to do so.
I'm guessing you needed to run ldconfig, which was probably done for you by another update.

---

### Post by RobotGymnast on 2011-04-08
> **Temüjin said:**
> Copying files directly into /usr/lib like that is not recommended. I would recommend you remove the file you installed and just use sevenmachines' PPA, as everything is neatly .deb packaged and automatically updated for you. [https://launchpad.net/~sevenmachines/+archive/flash](https://launchpad.net/~sevenmachines/+archive/flash)


I'm guessing you needed to run ldconfig, which was probably done for you by another update.

Thanks for the warning, and the repo! In fact, my Youtube had stopped working as suddenly as it started, but using the package from the link you supplied made it better - and not only is it working, but Youtube looks much nicer than before.

---

### Post by RobotGymnast on 2011-04-08
AAARGH! Now it's quit working again. Reinstalling the package doesn't help.

Edit: It seems intermittent. I just tried refreshing the page four or five times and it started working.

---

### Post by Yellow Pasque on 2011-04-08
Usually, the 64-bit version is pretty stable. I'm not sure if the problem lies with chromium or the plugin. Maybe starting chromium from the terminal will produce helpful clues..

---

