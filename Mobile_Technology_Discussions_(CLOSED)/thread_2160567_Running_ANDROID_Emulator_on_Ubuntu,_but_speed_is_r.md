---
title: "Running ANDROID Emulator on Ubuntu, but speed is really slow?!"
date: 2013-07-07
forum: Mobile Technology Discussions (CLOSED)
---

### Post by satyamM on 2013-07-07
I am running Android Emulator, but its speed is hell slow. How to get rid of slow speed and make the working faster so that it almost gives a real time mobile phone feel...you know what I mean..!!...

So someone please help.

---

### Post by DeathByDenim on 2013-07-07
The only way to make it faster is to get a faster computer. You computer is trying to emulate a different platform (ARM), which takes a fair bit of computing power.
You might have some luck with increasing the RAM used by the emulator as detailed here: [http://stackoverflow.com/questions/4814992/honeycomb-android-emulator-is-dog-slow-will-it-get-manageable-before-the-offic](http://stackoverflow.com/questions/4814992/honeycomb-android-emulator-is-dog-slow-will-it-get-manageable-before-the-offic) , but yeah. It's slow.

---

### Post by mr john on 2013-07-09
The emulator in the Android SDK isn't very good. If you're developing apps it's better to use an actual phone or tablet. If you're not developing apps then I would try something else. On Windows "Bluestacks" is alot faster than the Android emulator. It runs at the speed you would expect and has some extra features which are nice, like Google Play. Maybe it will work with wine?

edit: I've read that Bluestacks wont work with wine.

---

### Post by satyamM on 2013-07-15
> **mr john said:**
> The emulator in the Android SDK isn't very good. If you're developing apps it's better to use an actual phone or tablet. If you're not developing apps then I would try something else. On Windows "Bluestacks" is alot faster than the Android emulator. It runs at the speed you would expect and has some extra features which are nice, like Google Play. Maybe it will work with wine?

edit: I've read that Bluestacks wont work with wine.


No WINDOWS!!!!!!! I only use Ubuntu 12.04 and have only Ubuntu as operating system..!!!

---

### Post by Nr90 on 2013-07-17
Have a look at [http://www.genymotion.com/](http://www.genymotion.com/)

---

### Post by satyamM on 2013-07-17
> **Nr90 said:**
> Have a look at [http://www.genymotion.com/](http://www.genymotion.com/)

I have tried GenyMotion. But its devices are not supporting Whatsapp(the chatting app). On every device, whenever I try to run Whatsapp, this message comes:** "Currently Tablets are not supported"**. So are GenyMotion devices only based on Tablet architecture? Any phone device? No?

---

### Post by audiofor on 2013-07-18
I have been working on an Android SDK for [the Nuxeo Content Management Platform]("http://www.nuxeo.com/en/products/enterprise-platform") in the past months (feel free to check out the early side of our developments in [my previous blog post on that topic]("http://blogs.nuxeo.com/dev/2011/03/android-client-for-nuxeo-dm.html"))  and have worked more on it lately as we are on our way to making the  first official release of this SDK. I wanted to share some feedback on a  practical side of Android development related to test and emulation.  After a few days of development, I found out that Android Emulator was a  pain because it is far too slow.
 First of all it is slow to boot, but even if you use Snapshot to  speed up the start, the execution is also very slow, especially when  using the debug mode.It is good for everyone and use.

---

### Post by T_N on 2014-02-03
@satyamM : Maybe that you have already found same solution. If not, then check if you have a CPU of Intel with Virtual Technology, then you can Install Intel Hardware Accelerated Execution Manager. It really speed your emulator up. You also need Intel x86 Emulator Accelerator (HAXM) for your Android AVD. The steps for configuration is written in this blog [http://hintdesk.com/android-how-to-speed-up-android-emulator/](http://hintdesk.com/android-how-to-speed-up-android-emulator/) . Just follow the instructions.

---

### Post by wangji on 2014-03-29
Could you try this :

[http://sourceforge.net/projects/toysbox/files/Android-CyanogenMod/](http://sourceforge.net/projects/toysbox/files/Android-CyanogenMod/)

there are quite a lot of live_iso ,live_usb and even package to install into user_home_dir_ubuntu (x32 as well as x64_Lubuntu)

The emulation runs quite smoothly, without using sdk or adt_bundle ,nor virtualbox or gennymotion ; just plain emulator-arm  

or plain x86_pc for android-x86-4.4.2.iso

---

### Post by jake_anderson28 on 2014-04-28
As referenced above, my guess would be that the processing power required is pretty substantial, and because of that you're either going to have to upgrade or give up on the emulator. Too bad there isn't a better solution.

---

### Post by sps828gaming on 2014-05-05
I think it all depends on RAM and processing power. My PC has 8gb of RAM and a 6 core proccesser and the Android emulator still runs extremly slow.

---

### Post by brunonova on 2014-09-22
This thread is a bit old, but I'll leave my experience here, nevertheless.

I've found the Android emulator to be much faster in Ubuntu than in Windows for some reason. It's actually faster than my Android phone!
But there are two things I always do when creating devices in the AVD:
[LIST]
[*]Enable "Use Host GPU"
[*]Choose a x86 CPU/ABI
[/LIST]
These are probably why it's fast in Ubuntu. But they don't have the same effect in Windows.

---

