---
title: "Converged Demo on Nexus 4"
date: 2013-07-30
forum: Mobile Technology Discussions (CLOSED)
---

### Post by hwttdz on 2013-07-30
Does anyone know of a demo (possibly youtube) of Ubuntu Touch running tethered/docked from a Nexus 4?  Note that the indiegogo video uses Ubuntu for Android (not the same thing).

---

### Post by grahammechanical on 2013-08-02
[http://www.ubuntu.com/tablet](http://www.ubuntu.com/tablet)

[http://www.omgubuntu.co.uk/2013/07/ubuntu-edge-convergence-shown-off](http://www.omgubuntu.co.uk/2013/07/ubuntu-edge-convergence-shown-off)

Why is Ubuntu for android not the same as Ubuntu touch? From the beginning it was made clear that the Ubuntu phone/tablet user interface would be sitting on Android and using Android video drivers. The Ubuntu edge devices will have one option that was not announced in the beginning, the ability to switch between Android and Ubuntu. That can only happen if Ubuntu and Android are using the same code.

---

### Post by hwttdz on 2013-08-02
Ubuntu for Android is installed as an app in the Android os.  So the Android kernel boots and Ubuntu runs on top of that.

In Ubuntu touch an Ubuntu kernel boots, it uses an lxc (Linux container) to load the hardware interfaces of Android so that Ubuntu touch is supported on most of the same hardware as Android.

I think what you might be referring to is the "unflipped" images where Ubuntu touch would use an Android kernel.  This has actually been on of the most active areas of development over the last few weeks so that the reference devices (the Nexus devices) are now using "flipped" images, where Touch is running on its own kernel and the few small Android bits are running in a Linux container.  This might give a slightly more comprehensible explanation than the one I just gave: [https://wiki.ubuntu.com/Touch/PortingFlippedInProgress#Differences_with_the_Porting_Guide_1.0](https://wiki.ubuntu.com/Touch/PortingFlippedInProgress#Differences_with_the_Porting_Guide_1.0)

Anyways, long story short, Ubuntu for Android != Ubuntu Touch (though they can both drive the unity 8 ui when docked).   I'm interested in a video showing unity running on Touch (preferably using a flipped image).

Edit:
I didn't address the last bit about the ability to switch between Ubuntu and Android.  If you're running Ubuntu for Android, you just close the Ubuntu app, and you're back in Android.  The process described in the Edge campaign is actually dual booting, i.e. you would have something like a bootloader, and could choose to boot either Android or Ubuntu, but no switching on the fly.  I never actually used wubi, but my impression was that it ran Ubuntu on top of Windows.  This would be similar Ubuntu for Android, where the Edge describes something more akin (in fact identical to) dual booting.

Double edit:
Confirmed by the development team, Ubuntu Touch cannot drive a docked device yet.  Development on that is scheduled for October.

---

### Post by Copper Bezel on 2013-08-02
That explains why the Edge campaign page refers to the Ubuntu-for-Ubuntu converged mode as a feature to be released after launch. Thanks for the clarification. I'm surprised, since I was operating on the assumption that Ubuntu is more or less Ubuntu and could probably run on top of itself more easily than on top of Android, but I understand why that's a serious understatement of what's actually happening in the converged mode (and never mind that Ubuntu Touch is not at all a complete product yet.)

The "flipped" stuff is interesting, too; I didn't realize that they'd managed to make it work without using the Android kernel already.

---

