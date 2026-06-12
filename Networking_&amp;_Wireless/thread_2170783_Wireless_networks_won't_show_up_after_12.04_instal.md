---
title: "Wireless networks won't show up after 12.04 install"
date: 2013-08-27
forum: Networking &amp; Wireless
---

### Post by mishe2 on 2013-08-27
Okay... I've been searching and working on a solution for this for a long time, but school started up again and I need the internet and don't have a lot of time, so I'm hoping for some help. I'm a beginner.
Wireless connections aren't showing up and I *don't* have the ability to use a wired connection. I've got an older computer and know this is a common occurrence, but everything I try doesn't work. Maybe I'm doing it wrong, so detailed instruction would be appreciated.

Thank you!

---

### Post by praseodym on 2013-08-27
Hi,

please open a terminal with CTRL+ALT+T and show the outputs of
```

lspci -nnk | grep -iA2 net
lsusb
iwconfig
lsmod
rfill list
```

---

### Post by mishe2 on 2013-08-27
Hey, thanks for replying. Here are the screenshots:




[ATTACH=CONFIG]245768[/ATTACH][ATTACH=CONFIG]245769[/ATTACH]

---

### Post by mishe2 on 2013-08-29
Anyone? I'd really like some help.

---

### Post by praseodym on 2013-08-29
You need this file, save it in "Downloads":

[http://de.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14ubuntu1_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14ubuntu1_all.deb)

Install it via:
```

sudo dpkg -i ~/Downloads/*.deb
```

---

### Post by chili555 on 2013-08-29
> **mishe2 said:**
> Anyone? I'd really like some help.Your wireless card requires firmware. Here is a post that attaches the firmware and explains how to install it without an internet connection: [http://ubuntuforums.org/showthread.php?t=2162973&p=12734362#post12734362](http://ubuntuforums.org/showthread.php?t=2162973&p=12734362#post12734362)

EDIT: Ooops!!  praseodym has you covered.

---

### Post by mishe2 on 2013-08-29
It's in the downloads folder, but it says:

dpkg: error processing /home/mishe/downloads/*.deb (--install):
cannot access archive: No such file or directory
Errors were encountered while processing:
 /home/mishe/downloads/*.deb

I tried opening it up in the software center but it won't let me install it there either.

---

### Post by mishe2 on 2013-08-29
> **chili555 said:**
> Your wireless card requires firmware. Here is a post that attaches the firmware and explains how to install it without an internet connection: [http://ubuntuforums.org/showthread.php?t=2162973&p=12734362#post12734362](http://ubuntuforums.org/showthread.php?t=2162973&p=12734362#post12734362)

EDIT: Ooops!!  praseodym has you covered.



Hey thanks,

I didn't see this until after trying Praseodym's suggestion. I tried this but after extracting on the desktop and running the first command it says:

cannot create directory ' /lib/firmware/b43': File exists

---

### Post by chili555 on 2013-08-29
> **mishe2 said:**
> 
cannot create directory ' /lib/firmware/b43': File existsThen just continue on with the next steps.

By the way, It's **D**ownloads, not downloads.

---

### Post by mishe2 on 2013-08-29
Ah. Thank you both *so* much!! I fixed it using praseodym's file, after doing **D**ownloads instead of downloads. You guys are awesome.

---

### Post by chili555 on 2013-08-29
We are glad it's working! [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

