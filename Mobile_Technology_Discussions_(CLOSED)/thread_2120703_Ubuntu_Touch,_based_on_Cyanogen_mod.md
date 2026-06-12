---
title: "Ubuntu Touch, based on Cyanogen mod?"
date: 2013-02-27
forum: Mobile Technology Discussions (CLOSED)
---

### Post by mr john on 2013-02-27
I've been reading some articles about the new Ubuntu for phones and tablets. Some of them are saying that it's a skin for Cyanogen mod.

[http://www.xda-developers.com/android/ubuntu-touch-next-generation-os-or-just-another-skin/](http://www.xda-developers.com/android/ubuntu-touch-next-generation-os-or-just-another-skin/)

[http://www.muktware.com/5273/ubuntu-touch-is-more-android-than-ubuntu](http://www.muktware.com/5273/ubuntu-touch-is-more-android-than-ubuntu)

I looked on [http://phablet.ubuntu.com/gitweb](http://phablet.ubuntu.com/gitweb) and saw at bunch of Cyanogen parts.


If this is true then the advantage is that it should be compatible with a large number of android handsets because Cyanagen works on alot of devices. The disadavantage is that that it may not be a full Ubuntu implementation that some people are expecting. Maybe they've found a way to sideload the Ubuntu OS into Cyanogen?

Maybe someone with more information can explain better what's going on under the hood?

---

### Post by grahammechanical on 2013-02-27
May be this will help

[http://www.jonobacon.org/2013/02/27/xda-developers-and-ubuntu-touch/]("http://www.jonobacon.org/2013/02/27/xda-developers-and-ubuntu-touch/")

Do not forget that Ubuntu is Open Source and just as there is nothing stopping others from taking the source code and modifying it, so there is nothing stopping Canonical from using the open source code of others.

We will have to wait until devices with Ubuntu Touch on them actually come out to see how close to a 'full Ubuntu implementation' there will be.

I see from the second link that FOSS people just cannot resist finding fault. 

Regards.

---

### Post by Nr90 on 2013-02-28
Have a look at:
[https://wiki.ubuntu.com/Touch/Porting](https://wiki.ubuntu.com/Touch/Porting)
The interesting bit is:
For quick reference, these are the current components used from Android:


Linux Kernel (stock Android kernel provided by the vendor, with a few changes to support some extra features needed by Ubuntu)
OpenGL ES2.0 HAL and drivers
Audio/Media HAL and services, to re-use the hardware video decoders
RILD for modem support
As Ubuntu is running in a separated container on top of an Android kernel and services, the communication between them happens via Binder, Sockets and libhybris.


Other than the very basic services (needed to re-use the binary blobs already available), the rest is just pure Ubuntu goodness

---

### Post by johnciaccio on 2013-03-03
I think it is more like cyanogen mod is based on Ubuntu. Since both are Linux variants. That first line is just a joke by the way. 

Since Ubuntu Touch does not use the Dalvic Java virtual machine for its interface or apps then if it is using any cyanogenmod code it would not be in the ui or anything visual. However since some cyanogenmods coding has been used in android and android has been used in Linux kernel etc. there is some common elements in all three probably.

It's in Ubuntu's best interest to have have the os developed as fast as possible and if that means using some work done by another developer then it's fine as long as it is open source. 

I believe the code will get more customized as the OS progresses. Remember that all of these are using Linux and there have been standards developed so things may look very much the same between them.

But to say Ubuntu Touch is just Cyanogenmod with a skin on it would have to be false since Ubuntu does not use a virtual machine to run it ui or apps.

Just my thoughts...please don't flame :)

---

### Post by Goff256 on 2013-03-05
My guess is that it's only starting off with Cyanogen mod, if only in the "we're taking this code and making our shiz out of it" sort of way.

Of course, I'm saying this based on the idea that Canonical is working on features in the background before they show them off at release. Can't hardly do that with "just cyanogen mod".

So, yes, it is based on it.

---

### Post by Nr90 on 2013-03-06
The porting guide mentions that you could also start with AOSP sources. It's just easier with cyanogen mod.
Therefor I'd say its not really based on it. It just uses android parts that are easy to get from the CM build.

---

### Post by pprice on 2013-03-08
I like the fact that this is built from CM. That means it can be flashed through recovery just like any other custom ROM. This makes it much easier to backup and restore to your current set-up when you want to test out Ubuntu without losing all of your data.

---

### Post by maxalman on 2013-03-09
> **pprice said:**
> I like the fact that this is built from CM. That means it can be flashed through recovery just like any other custom ROM. This makes it much easier to backup and restore to your current set-up when you want to test out Ubuntu without losing all of your data.

That's what I do every time a new update is released.:)

---

### Post by PerplexxdYet on 2013-03-11
Huh. I really wouldn't mind that it's based on CM, as CM is pretty stable and I enjoy it.

---

### Post by KoRnKloWn on 2013-05-27
I don't get why people think Ubuntu Touch would have been developed from the ground up? They must not understand open source, was Ubuntu developed from the ground up? No, it was built off of Debian, that's kinda the way things work,it's the whole point of open source software. Did they also forget that Unity was built off of Gnome? They know that wasn't made from scratch too right? KDE was built from Qt, the list goes on and on.

And about the credit thing, in a commercial you are trying to show what's *different*, not what's the *same*. Have you ever seen an Android commercial advertise Linux? No, what about Java? I haven't, I'm sure when everything's said and done they'll give Cyanogenmod their credit, and I'm sure the credits are in the code.

Sorry for the rant :P, I just don't get why people make such a big deal about this.

---

### Post by AntontheGreek on 2013-06-09
One must remember that the Android Kernel is a fork of the mainline Linux kernel that Ubuntu has been using since 2004 and has been around since 1991.
The best source for Android kernels with proprietary blobs or binary drivers for specific target devices is CyanogenMod as those devs have extracted the kernel for people to build from source.
Of course, when an Ubuntu Touch device goes into development for commercial sale, the manufacturer would take the Linux Kernel, tweak and add necessary drivers to deliver maximum performance on the hardware as is currently done with Android devices.
So if anyone wants to accuse Canonical/Ubuntu of "stealing" any part of Android or CyanogenMod, ask where the kernel came from.

---

