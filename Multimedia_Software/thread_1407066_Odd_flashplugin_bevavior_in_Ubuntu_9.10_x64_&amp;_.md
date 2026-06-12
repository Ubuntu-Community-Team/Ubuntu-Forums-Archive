---
title: "Odd flashplugin bevavior in Ubuntu 9.10 x64 &amp; firefox 3.5"
date: 2010-02-14
forum: Multimedia Software
---

### Post by cpufreak2589 on 2010-02-14
I'm having a twofold problem with flash that is driving me absolutely crazy. The first problem is that randomly flash will cease to work and every flash video I may have open in any instance of firefox will turn to a white box. Reloading the page will fix this issue.

The second issue is more serious, as most flash applets (whatever the word is) will not allow me to interact with them. Example: I am on a page with an embedded youtube video with the giant play button in the middle of the page. I can click on the play button and it will go through the onclick depression animation, and when I release the button will go through the release animation, but nothing will happen. It it like I am interacting with the gui but no actual code is being executed. I can browse youtube videos from youtube directly, but any embedded flash content will not work. This is also the case with other sites like megavideo. Some web sites based entirely in flash will not work either. I have completely purged flashplugin-nonfree from my system and reinstalled through synaptic.

EDIT: I solved the problem by editing /usr/lib/nspluginwrapper/i386/linux/npviewer and adding export GDK_NATIVE_WINDOWS=1 before the last line of text. Odd how I can't close my own thread or edit the tag.

---

### Post by lovinglinux on 2010-02-14
The big play button indicates that you have gnash or swfdec plugin installed (I don't remember which one). So uninstall it with these commands:

```
sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree

```

Since you have 64bit Ubuntu, follow [this tutorial](http://ubuntuforums.org/showthread.php?t=1358591) to install the 64bit version of flash.

This should solve all your problems.

---

### Post by Psychoscorpic on 2010-02-16
Thanks - your npviewer line worked for me! (Flash sites suddenly became blank screens - I think the plugins got updated in the last few days & something broke)

---

