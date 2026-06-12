---
title: "Help with ATI Visiontek Radeon HD4870 driver install"
date: 2009-02-12
forum: Multimedia Software
---

### Post by mikenchi on 2009-02-12
Hello all:

I recently installed Ubuntu 8.10 on my home-made system running an ASUS P5B Plus mobo. I had been running a Sapphire Radeon X1650 Pro for a while, and had installed the drivers supplied by ATI with no problem. I recently upgraded to the HD4870. Before changing the video cards, I did not remove the old drivers from Ubuntu. The first time I booted up, it did not work, video was scrambled. So I reset system, did a recovery boot from the grub menu, and chose to fix the X Server. This worked, video displayed normally. I then downloaded and installed the HD4870 package from ATI. After installing and rebooting, I get scrambled video again so I had to do the X Server fix. 

I am now looking in Synaptic package mgr to remove the drivers and start over. When I search for ATI in the mgr, it shows quite a few things, so I wanted to make sure I am removing the right thing so I don't destroy this build. I believe these are the ones I want to remove but can anyone advise if I'm right? 

These are showing as currently installed:
xserver-xorg-video-ati
X.Org X server -- ATI display driver wrapper

AND

xserver-xorg-video-radeon
X.Org X server -- ATI Radeon display driver

I'm not sure if these are the ones I installed from ATI, or if these came with Ubuntu and are required system components that should not be messed with.

Thanks much in advance!

---

### Post by markbuntu on 2009-02-12
The ati driver you previously installed has its own script to remove it in usr/share/ati. I think it is fglrxuninstall.sh or something like that. Just open a terminal and go to the directory and sun the scipt as root
cd /usr/share/ati
sudo sh ./fglrx-uninstall.sh 

or whatever it is.
then reboot and run the installer for the new one etc.

---

