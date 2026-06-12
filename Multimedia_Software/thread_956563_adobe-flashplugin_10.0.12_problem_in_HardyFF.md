---
title: "adobe-flashplugin 10.0.12 problem in Hardy/FF"
date: 2008-10-23
forum: Multimedia Software
---

### Post by MountainX on 2008-10-23
I'm running Hardy 32bit with FF 3.0.3. I installed adobe-flashplugin 10.0.12 directly from adobe and used the installation instructions for .deb files located here: [http://www.adobe.com/products/flashplayer/productinfo/instructions/](http://www.adobe.com/products/flashplayer/productinfo/instructions/)

After installing, about:plugins gives the following info:
Shockwave Flash File name: libflashplayer.so, Shockwave Flash 9.0 r124

I do have ubuntu-restricted-extras installed. Could that be the problem?

The only relevant file I find on my system is here:
/usr/lib/adobe-flashplugin/libflashplayer.so (dated 2008-10-06)
I do not have a folder named /home/<username>/.mozilla/plugins

I appreciate any help getting flash-10 installed properly. Thanks.

---

### Post by MountainX on 2008-10-23
resolved, but not without a lot of pain...
I can't say what single thing I did or what series of steps ultimately helped resolve it. 

I did have to close firefox **before** installing the deb.
I did have to manually delete existing files too!
And I had to repeat the process a dozen times. :(

Here are some links I found during my efforts:
```
http://adventuresinswitching.blogspot.com/2008/10/flash-10-is-out-for-linux-and-ubuntu.html
http://www.ubuntugeek.com/how-to-install-adobe-flash-player-10-in-ubuntu-804-hardy-heron.html
http://www.cyberciti.biz/tips/linux-install-flash-player-10.html
http://tombuntu.com/index.php/2008/05/16/test-drive-flash-player-10-beta-in-ubuntu/
http://tombuntu.com/index.php/2008/08/28/test-drive-adobe-flash-player-10-rc-in-ubuntu/
http://markusthielmann.com/blog/flash_10_beta_ubuntu_hardy
http://ubuntuforums.org/showthread.php?t=766683
```

---

### Post by gandaran on 2008-10-23
> I do have ubuntu-restricted-extras installed. Could that be the problem?

yes, this meta package installs the **flashplugin-nonfree** (adobe flash 9)
you can remove the flashplugin-nonfree in synaptic package manager safely without removing the rest.

---

### Post by MountainX on 2008-10-25
All my prior attempts DID NOT WORK.

Today I finally managed to get it working with these steps:

```
sudo apt-get remove libflashsupport
sudo apt-get remove flashplugin-nonfree
wget http://fr.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_10.0.12.36ubuntu1_i386.deb
sudo gdebi flashplugin-nonfree_10.0.12.36ubuntu1_i386.deb
```

I think the credit for the above belongs to this thread: [http://ubuntuforums.org/showthread.php?p=6030814#post6030814](http://ubuntuforums.org/showthread.php?p=6030814#post6030814)

---

