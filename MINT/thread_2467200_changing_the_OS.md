---
title: "changing the OS"
date: 2021-09-18
forum: MINT
---

### Post by corvairbob on 2021-09-18
i have linux mint on a Eee pc laptop. i downloaded linufx on that drive can i install the linuxfx over mint or do i have to down linuxfx onto a thumb stick like i did with mint and then boot to the stick and go from there? i'm trying to find a linux type OS that works more like windows does so when i need to install or run a program i do not have to spend hours keyboarding to get it to run. i see linuxfx and also robolinux they say runs like windows and even can run windows type programs.

so for installing another OS in linux will i have to put them on a stick in iso format and then boot to that stick and install that OS that way? it is not an issue i just need to make sure how to go about it for any of the linux OS i try to test out.  thanks

---

### Post by mikewhatever on 2021-09-18
This is an odd query, as it has nothing to do with Ubuntu. Why did you think is was a good idea to ask here?

---

### Post by ubfan1 on 2021-09-18
There are ways to boot the ISO off the hard disk, but probably not if you are overwriting the partition the ISO is on. The stick is more straightforward, since the hdd grub boot instructions may differ by distribution.

---

### Post by deadflowr on 2021-09-18
*Thread moved to **MINT***

---

### Post by corvairbob on 2021-09-18
ok i tried to install with dual boot and that failed bad. so i took the drive out and formatted it  and ran rufus about 50 times before it finally took.  and now i have to jump thru a few hoops but it looks like it is now going thru the setup configuration. i will stop back and let you know how this works.

---

### Post by guiverc on 2021-09-18
You're speaking about a system I don't know so I'll speak in terms I do know about (ie. Ubuntu).

Ubuntu is available in many forms, with different installers - they have have different capabilities.  Installers can be `ubiquity`, `debian-installer`, `subiquity`, `calamares` etc..  The ISO you download and use dictates which installer is provided for that release or *flavor* you use for Ubuntu.

Can you boot an ISO from hdd/sdd - yep.  I have an thinkpad with dead USB drives, and I didn't want to use DVDs for QA (*Quality Assurance*) testing, so I'd copy the ISO to the disk (`scp`) of the thinkpad, then run a script on it and the ISOs would appear in `grub` allowing me to boot and run the ISO.  I did the same on an eeepc too, but only rarely, so I know this works there.

The `ubiquity` installer (*this may depend on release, but you weren't specific as to installer so I'm using this as example*) will **not** let you install to the partition it booted from - ie. I'd install to a different partition - which was fine for my purposes anyway (*I didn't have to re-setup my ISO boot structure!*), and would **not** full-disk install as it refused to overwrite the partition where the ISO was booted from (*again I felt this was useful as I didn't want this either*).

What I'm describing with `ubiquity` may impact your non-Ubuntu OS using an *unknown* installer for *unstated* release.  Different installers have different restrictions, different solutions for issues etc.

You'll likely find you can do whatever you want; but the setup of what I describe, I did only because the thinkpad (t42p) didn't have bootable USB ports - I'd have just used a thumb-drive if it did as it would have been easier (no `scp` & script run to test; just boot thumb-drive I already had written for testing on other devices..). Using a USB-thumb drive maybe easier.

---

### Post by corvairbob on 2021-09-19
ok i see it got moved to mint. i looked for mint and did not see that area. so i will again look and see what they say thanks

---

### Post by corvairbob on 2021-09-19
so where is mint on this forum? i do not see it under forum community. can you help me get to that forum? thanks

---

### Post by coffeecat on 2021-09-19
Look at the top of this page - you'll see the complete navigation trail as a series of links. Everything on this forum is under "The Ubuntu Forum Community". Sub-ordinate to that are the four main sections of the forum. You are now in a sub-forum of a sub-forum, etc, of the fourth, "Other Discussion and Support". This thread was moved because you posted in one of the first two main sections which are for Ubuntu and recognised flavours only. Mint is not Ubuntu, neither is it a recognised flavour. Mint has its own forum, here: [https://forums.linuxmint.com/](https://forums.linuxmint.com/)

---

### Post by T6&amp;sfpER35% on 2021-09-19
> [COLOR=#000000] i'm trying to find a linux type OS that works more like windows[/COLOR]
i'm confused right there 
> [COLOR=#000000]i do not have to spend hours keyboarding to get it to run[/COLOR]
huh? i never spend hours to get an installed program to run , you click it and it opens in milliseconds

---

### Post by QIII on 2021-09-19
>  i'm trying to find a linux type OS that works more like windows does so when i need to install or run a program i do not have to spend hours keyboarding to get it to run.

Are you talking about native Linux applications or Windows applications?  Linux is not Windows.  Windows applications cannot be installed on Linux except as I describe below. Installation of applications in most distros, as mentioned above, is point-and-click in most cases, although some applications are not available in any given distribution's package databases for any number of reasons.  You might even be able to use *some* Windows apps using either Wine or Mono, but that is hit or miss.  Not all applications work equally well.

> i see linuxfx and also robolinux they say runs like windows and even can run windows type programs.

Those distributions do not run Windows programs natively.  They each include a pre-configured Virtual Machine application onto which you may install Windows.  There are a number of VM applications, such as VMWare, Xen and VirtualBox.  All Linux versions contain in their kernels KVM (Kernel-based Virtual Machine) into which Windows can be installed.  I have such a Windows virtual machine on this computer even now, along with eleven others.  To run a virtual machine, it is not necessary to leave your Linux session, but it is necessary to start the VM and use its GUI.

Neither of those distributions does anything that Ubuntu cannot.

---

