---
title: "USB Headset Crashes Ubuntu 10.04"
date: 2011-07-11
forum: Multimedia Software
---

### Post by gmjs on 2011-07-11
Hello,

I've just purchased a USB headset and wanted to use it with my Ubuntu 10.04 installation.

Unfortunately, upon inserting the USB headset into a USB port, Ubuntu freezes (you can still move the mouse, but it doesn't seem to respond to the keyboard and the GNOME interface doesn't respond at all).

If I boot the computer with the USB headset connected, Ubuntu stalls at the usplash screen.

If I boot into the recovery mode and plug in the headset, the terminal also stops responding.  I waited and was presented with the message:

```
BUG: CPU#1 soft lockup stuck for 61s!
```

Does anyone have any ideas at all as to how I should start to debug this issue?  It seems very strange that it should cause a lock up.

Incidentally, the headset is a Sennheiser PC36 and works in Windows and another Linux distribution (Arch).

Many thanks.

---

### Post by gmjs on 2011-07-17
It appears that the updated kernel (2.6.32-32) doesn't play nicely with the USB headset.

After switching back to kernel 2.6.32-31, I can use it successfully.

---

### Post by gmjs on 2011-07-21
It looks like I was just unlucky (again)!  The lastest kernel update from Ubuntu for 10.04 (2.6.32-33) is also happy with the USB headset.

---

### Post by mm.ie on 2011-07-31
Hi guys, I see that this thread is deemed [solved] but I have exactly the same problem.

I am using 


2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:05:41 UTC 2011 i686 i686 i386 GNU/Linux

Anyone any idea?  BTW the headset works fine.  It is recognized and become available for selection within sound manager.

mm.ie

---

### Post by gmjs on 2011-07-31
I've just had a thought . . . 

I've always installed an alsa backport for my sound card (you cannot change the volume without sound pausing for 10-20 seconds without it).

I'm wondering now if that was the problem (the package is specific to each kernel release--hence the problem disappearing after the upgrade).

Do you install a 'backports' package for alsa for any reason via 'aptitude'?  If so, there's the answer.

Thanks.

---

### Post by gtimuss on 2011-12-05
This is the bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/618155](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/618155)

---

