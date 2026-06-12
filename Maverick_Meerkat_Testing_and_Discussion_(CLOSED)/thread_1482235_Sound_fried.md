---
title: "Sound fried"
date: 2010-05-13
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by tad1073 on 2010-05-13
After the few updates this morning, there is a bunch of static with sound using the card listed below.
```
*-multimedia
       description: Multimedia audio controller
       product: VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller
       vendor: VIA Technologies Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ICE1724 latency=64
       resources: irq:21 ioport:ef00(size=32) ioport:ee00(size=128)

```
that is all I can give for now, don't know how to investigate further.

---

### Post by ranch hand on 2010-05-13
I am having no trouble with mine.  It may be specific to your controller.

File a bug.

---

### Post by tad1073 on 2010-05-13
> **ranch hand said:**
> I am having no trouble with mine.  It may be specific to your controller.

File a bug.

```
*-multimedia            
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:22 memory:fdff4000-fdff7fff

```
Works fine, but the card in my original post is the one in question.

Will file a bug report.

---

### Post by taavikko on 2010-05-13
Have you tested with "new user" that something just haven't corrupted your ~/.pulse*

/var/log/apt/history.log gives details about packages upgraded.
But there's been none related to sound in few days if I recall correctly.

---

### Post by tad1073 on 2010-05-13
> **taavikko said:**
> Have you tested with "new user" that something just haven't corrupted your ~/.pulse*

/var/log/apt/history.log gives details about packages upgraded.
But there's been none related to sound in few days if I recall correctly.

```
Start-Date: 2010-05-13  03:38:11
Purge: tomboy (1.2.1-0ubuntu1)
End-Date: 2010-05-13  03:38:20

Start-Date: 2010-05-13  03:38:53
Install: libpanelappletmm-2.6-1c2 (2.26.0-1), libboost-system1.40.0 (1.40.0-4ubuntu4), libpcrecpp0 (8.02-1), libgconfmm-2.6-1c2 (2.28.0-1), libdbus-c++-1-0 (0~20090907-1), gnote (0.6.2-2ubuntu1), libboost-filesystem1.40.0 (1.40.0-4ubuntu4)
End-Date: 2010-05-13  03:39:03

Start-Date: 2010-05-13  03:57:03
Install: python-twisted-words (10.0.0-2), gm-notify (0.10.2-1~ppa1)
End-Date: 2010-05-13  03:57:11

Start-Date: 2010-05-13  04:07:41
Remove: python-twisted-words (10.0.0-2)
Purge: gm-notify (0.10.2-1~ppa1)
End-Date: 2010-05-13  04:07:46

Start-Date: 2010-05-13  04:08:21
Install: python-chardet (2.0.1-1), python-utidylib (0.2-3.2ubuntu2), python-feedparser (4.1-14), libtidy-0.99-0 (20091223cvs-1)
End-Date: 2010-05-13  04:08:31

Start-Date: 2010-05-13  04:16:32
Install: python-twisted-words (10.0.0-2), gm-notify (0.10.2-1~ppa1)
End-Date: 2010-05-13  04:16:42

Start-Date: 2010-05-13  04:21:37
Install: ubuntu-tweak (0.5.4.1-1~lucid1)
End-Date: 2010-05-13  04:21:47

Start-Date: 2010-05-13  04:24:19
Remove: linux-image-2.6.32-21-generic (2.6.32-21.32), linux-headers-2.6.32-21-generic (2.6.32-21.32), linux-headers-2.6.32-21 (2.6.32-21.32)
End-Date: 2010-05-13  04:24:34

Start-Date: 2010-05-13  10:12:07
Upgrade: libpam0g (1.1.1-3ubuntu1, 1.1.1-3ubuntu2), libpth20 (2.0.7-14, 2.0.7-16), libxcb1 (1.5-2, 1.6-1), libpam-modules (1.1.1-3ubuntu1, 1.1.1-3ubuntu2), libpam-runtime (1.1.1-3ubuntu1, 1.1.1-3ubuntu2), libxcb-render0 (1.5-2, 1.6-1)
End-Date: 2010-05-13  10:12:25

Start-Date: 2010-05-13  12:17:14
Install: libbabl-0.0-0 (0.0.22-1build1), libgegl-0.0-0 (0.0.22-0ubuntu4), gimp-data-extras (2.0.1-3), gimp (2.6.8-2ubuntu1.1), libgimp2.0 (2.6.8-2ubuntu1.1), gimp-data (2.6.8-2ubuntu1.1)
End-Date: 2010-05-13  12:17:56
```

last few hours from /var/log/apt/history.log

---

### Post by taavikko on 2010-05-13
You ran an partial upgrade...?
Removed the latest official kernel...

Unless you're running alternative kernel?

---

### Post by tad1073 on 2010-05-13
:~/Desktop$ uname -a
Linux thomthom 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux

no partials, kernel above

and new user has same effect...

---

### Post by taavikko on 2010-05-13
> **tad1073 said:**
> :~/Desktop$ uname -a
Linux thomthom 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux

no partials, kernel above

and new user has same effect...

All that caughts my eye, is the kernel in use.
*.22 is from proposed repos (lucid) (proposed not in use with MM)

Did this start after removing the *.21 kernel...

---

### Post by tad1073 on 2010-05-13
> **taavikko said:**
> All that caughts my eye, is the kernel in use.
*.22 is from proposed repos (lucid) (proposed not in use with MM)

Did this start after removing the *.21 kernel...

yup

I need to re-install .21 and remove .22?

I have sound through onboard audio and just of static with the sound card mentioned in my first post.

---

### Post by cariboo on 2010-05-13
Do you still get static, if you disable onboard sound?

---

### Post by tad1073 on 2010-05-13
> **cariboo907 said:**
> Do you still get static, if you disable onboard sound?

yes

---

### Post by tad1073 on 2010-05-13
I removed .22 kernel and installed .21 and the problem is fixed so, there is a problem with the .22 kernel and sound on 10.10 but I wouldn't know how to nail it down.

should I mark this as solved?

Seing how it is just a work around, I am thinking no, what about the rest of you?

---

