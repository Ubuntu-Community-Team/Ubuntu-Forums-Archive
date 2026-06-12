---
title: "Xubuntu 13.04 64bit + Skype Nightmare"
date: 2013-05-06
forum: Multimedia Software
---

### Post by slumbergod on 2013-05-06
I've had nothing but problems with Xubuntu 13.04 and combined with Skype in the official channels (Canonical Partner) it has been a constant headache. 

I finally have Skype working properly so I am posting what I did in case others reach desperation point.

First, the default kernel is buggy. Sound keeps breaking for me and my webcam keeps going super dark. 
This guy's solution lets you upgrade to a newer (and so far less buggy) kernel:
[http://blog-darryldias.rhcloud.com/2013/05/installupgrade-to-linux-kernel-3-9-stable-in-ubuntulinux-mint/](http://blog-darryldias.rhcloud.com/2013/05/installupgrade-to-linux-kernel-3-9-stable-in-ubuntulinux-mint/)

cd /tmp
wget [http://dl.dropbox.com/u/47950494/upubuntu.com/kernel-3.9](http://dl.dropbox.com/u/47950494/upubuntu.com/kernel-3.9) -O kernel-3.9
chmod +x kernel-3.9
sudo sh kernel-3.9
sudo reboot

Second, uninstall skype completely. Purge it. Then go into Synaptic and remove Canonical Partners. Reload your lists. This will stop the older version you can install from being updated. Since those monkeys at Microsoft took over Skype it has become massively bloated and less and less reliable. The headaches trying to get it to work are just unreal. Solution roll back to an older version that might work for you:

wget -O skype [http://download.skype.com/linux/skype-ubuntu_4.0.0.8-1_amd64.deb](http://download.skype.com/linux/skype-ubuntu_4.0.0.8-1_amd64.deb)
sudo apt-get install libxss1 lib32stdc++6 lib32asound2 ia32-libs libc6-i386 lib32gcc1 (which must make skype one of the most bloated pieces of crapware out there...combined total over 100mb)
sudo dpkg -i skype

Anyway, maybe it will help you. At least I now have a webcam with normal looking brightness and contrast.

I can't help but wonder if the decision to reduce the amount of testing pre-release versions get is going to bite Canonical in the behind. 13.04 should be named Buggy Blowfly

---

