---
title: "Ethernet chip dead need to download wireless driver for 10.10 manually"
date: 2010-10-11
forum: Networking &amp; Wireless
---

### Post by linuxcool on 2010-10-11
Hello everyone,
I picked up an Acer 4710Z Laptop with Broadcom BCM 4311 wireless very cheaply because the ethernet chip died.
OK if I boot up live or installed Mepis 8.5 the wifi works because the driver is included.
Ubuntu most likely for legal reasons can't include these drivers.
I know in the pass on other Laptops that when Ubuntu detects that a driver isn't install, a pop up appears giving you the option to install the require driver and away you go. I can't do this due to having no wired internet.
What I need from you is a url link to the repository where the restricted drivers are located so I can download it get my wireless working then go to Ubuntu normal repository and install extra apps etc.

Ubuntu 10.10 wireless driver needed. ( Broadcom BCM 4311 )

---

### Post by solar george on 2010-10-11
You'll need;
[http://gb.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.1.1.2-3ubuntu1_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.1.1.2-3ubuntu1_all.deb)
[http://gb.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb)
[http://gb.archive.ubuntu.com/ubuntu/pool/main/f/fakeroot/fakeroot_1.14.4-1ubuntu1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/f/fakeroot/fakeroot_1.14.4-1ubuntu1_i386.deb)
[http://gb.archive.ubuntu.com/ubuntu/pool/main/p/patch/patch_2.6-2ubuntu1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/p/patch/patch_2.6-2ubuntu1_i386.deb)

---

### Post by linuxcool on 2010-10-12
Hello solar george,
I installed the packages while running live but wireless wasn't detected. Is there a command I can run to see if these packages work as I don't want to wipe my Mepis install unless I know these work for sure.

Thank you for taking the time to post these links.

---

### Post by solar george on 2010-10-12
I'm not sure, since it sounds like you've got the card as an addon could you try removing it and reconecting it.

---

### Post by linuxcool on 2010-10-12
Hello solar george,
As far as i know it's built inside the Laptop and not a plug in card?
I haven't opened the laptop to look if its built in to the mother board.

I'll experiment a bit more. If all else fails I'll just use Mepis.

---

### Post by solar george on 2010-10-13
I was just looking for an easy way to trigger the driver loading - if you have an rfkill switch (turns all wireless on or off) try switching that about while in the live system.

It would be much easier if you had an installed system as a simple reboot would remove the need for this messing around.

---

### Post by linuxcool on 2010-10-14
Hello solar george,
In the end I've installed Kubuntu 9.10 Netbook Remix as it came with the correct wireless drivers already installed. Stupid thing is the during the install process it uninstalls them? (Legal Reasons I guess) Had to fiddle and reinstall them off the CD but got it working in the end. Thank you for taking the time to answer my request.:)

I know 9.10 is now a year old but for what I do it's fine. Google Chrome, latest Adobe Flash installed correctly so my wife can Facebook etc.

I must say I tested a lot different Distro's in the search for something suitable who's developers need to sit down and take a good hard look at what their offering as a newbie would be scared back to Windows. These Distro's do Linux no favors and are a step backwards.

Ubuntu is about the user experience, it's not good enough just to bring a large number of apps together and hope a user can work it all out for themselves. You should never include an app that looks like it came out 20 years ago no matter how useful it is. Give it a better GUI at least.

---

### Post by solar george on 2010-10-14
Well I'm glad you found something that works, although I'd strongly suggest the you upgrade to 10.04 (a lot less bugs in Kubuntu's netbook version). The reason that you found the drivers were removed in the installation is due to the fact that the install copies the read-only filesystem off the cd and I assume that attempting to keep changes from the ramdisk would not be reliable (or in some cases desireable) enough to put in the work needed to add the feature.

WRT. the large number of different distros that's just a result of the option anyone with sufficiant knowladge has with open source software of making their own version if they don't feel that their needs are catered to. And on the whole its a good thing - no team can tie people into their distro but some distros can focus on ease of use, making default choices for everything while others require you to choose and setup your software all by yourself.

---

### Post by linuxcool on 2010-10-14
Hello solar george,
My wife runs Ubuntu 10.04 Remix on her EeePC. My 6 year old daughter runs ubuntu 10.04 on her Desktop. My 4 year old daughter runs "Legacy OS" on her old Desktop (Todays Software for yesterday's Hardware). We are Linux through and through.

---

