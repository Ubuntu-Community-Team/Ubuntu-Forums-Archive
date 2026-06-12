---
title: "Vista, Wubi Lucid, Maverick Alpha 3"
date: 2010-08-24
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by santana007 on 2010-08-24
I dual boot with Vista and a Wubi install of Lucid. I would like to install 10.10 Alpha 3 (in a separate partition). Will Grub allow a *triple* booting among all 3 O.S's or will I lose the option to boot into Lucid?

Thanks in advance.

---

### Post by stlsaint on 2010-08-24
You can boot as many OS's as your harddrive can handle! (meaning the size of the drive can handle all the os's!)

---

### Post by Rubi1200 on 2010-08-24
> **stlsaint said:**
> You can boot as many OS's as your harddrive can handle! (meaning the size of the drive can handle all the os's!)
+1
with one caveat; you can only have 4 primary partitions on most modern drives. But you could create an extended partition and, in theory, as many logical partitions within that as you wanted.

Hope this helps.

---

### Post by bcbc on 2010-08-24
The maverick grub will take over, and you will have to select windows first, before being able to boot the wubi install. 

I don't recommend you install Maverick unless you are consider your machine a test machine i.e. can handle losing everything. Also, you should post all maverick related posts in the [Maverick forum]("http://ubuntuforums.org/forumdisplay.php?f=385") and read the stickies there.

---

### Post by sipherdee on 2010-08-28
Thanks for this thread, I was also wondering if it was possible to use Wubi twice to test Maverick Meerkat with an existing Lucid Lynx installation.

---

### Post by bennachie on 2010-08-28
No, that won't work. What would work (and quite safely) would be to set up a dual boot with Windows and Lucid, and then replace the Wubi installation of Lucid with a similar installation of Maverick.

The only problem is that some people have experienced difficulty installing Maverick Alpha 3 with Wubi under Windows 7. I haven't tried this since the ISO testing period, so the issue may well have been overcome in the daily builds (and the Beta version is due out next week anyway).

---

### Post by bcbc on 2010-08-28
> **bennachie said:**
> No, that won't work. What would work (and quite safely) would be to set up a dual boot with Windows and Lucid, and then replace the Wubi installation of Lucid with a similar installation of Maverick.

The only problem is that some people have experienced difficulty installing Maverick Alpha 3 with Wubi under Windows 7. I haven't tried this since the ISO testing period, so the issue may well have been overcome in the daily builds (and the Beta version is due out next week anyway).

Maverick wubi is still not working on any version of windows. There is a bug report ([https://bugs.launchpad.net/wubi/+bug/600578](https://bugs.launchpad.net/wubi/+bug/600578)) you can follow - but since there has been no response from the devs I would assume it is still not working.

---

### Post by bennachie on 2010-08-29
@bcbc

Thanks for the update - I'm actually listed as a subscriber to that bug already, but, for some reason, your most recent comment didn't reach my mailbox.

---

