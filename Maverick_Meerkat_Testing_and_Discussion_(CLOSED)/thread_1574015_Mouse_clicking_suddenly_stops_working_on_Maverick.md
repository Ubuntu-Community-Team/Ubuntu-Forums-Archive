---
title: "Mouse clicking suddenly stops working on Maverick"
date: 2010-09-13
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Ancanus on 2010-09-13
Forking from [this thread]("http://ubuntuforums.org/showthread.php?t=1572412") as it may not be the same issue.

While doing menial tasks (firefox, gedit,) my mouse clicking will suddenly stop working. I am still able to move the mouse cursor, and I am still able to operate the machine perfectly using the keyboard. It is just the mouse clicking that is affected.

To workaround this, I can shortcut a terminal open and do *sudo service gdm restart* and everything will be working until it occurs again.

How can I get the necessary information to bug-report this?

---

### Post by Bastanteroma on 2010-09-13
I'm not sure this is right, but I reported my somewhat similar [bug]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/636246") by following these [instructions]("https://help.ubuntu.com/community/ReportingBugs"), using "xorg" as the package when I ran ubuntu-bug. Good luck.

---

### Post by cariboo on 2010-09-13
> **Ancanus said:**
> Forking from [this thread]("http://ubuntuforums.org/showthread.php?t=1572412") as it may not be the same issue.

While doing menial tasks (firefox, gedit,) my mouse clicking will suddenly stop working. I am still able to move the mouse cursor, and I am still able to operate the machine perfectly using the keyboard. It is just the mouse clicking that is affected.

To workaround this, I can shortcut a terminal open and do *sudo service gdm restart* and everything will be working until it occurs again.

How can I get the necessary information to bug-report this?

Does anything show up in /var/log/messages and/or /var/log/kern.log?

---

### Post by Ancanus on 2010-09-15
> **cariboo907 said:**
> Does anything show up in /var/log/messages and/or /var/log/kern.log?

Nothing worthwhile, at least.

However, I found another workaround:
When the mouse stops working, I click on my touchpad and the mouse starts working again.

---

### Post by kmas on 2010-10-01
i'm having a different issue, but i think it could be taken in same context

my touchpad right click doesn't work. I have a button on my key board for right click, but doesn't right click on items mouse pointer hovers. I also went into synaptic and found an annoying work around, i enable right click with long click, so basically after 2 seconds left clicking right click menu context shows up, any one on what to do to troubleshoot this?

here's a complete report of my hard info: [http://dl.dropbox.com/u/1567633/hardinfo_report.html](http://dl.dropbox.com/u/1567633/hardinfo_report.html)forgot to mention the most important part, i'm on maverick RC AMD 64

ruling out the possibility of it failing because of something i installed, this is a fresh install, ruling out hardware issue, mouse works well under windows. for troubleshooting sake, switched from right handed to left handed, the right click (select) works fine, but the left click (menu) wouldn't bring menu up. I know it has to do with the touchpad configuration on my laptop because USB mouse works. 

cross referencing posts in which i posted this comment: [http://ubuntuforums.org/showpost.php?p=9911677&postcount=52](http://ubuntuforums.org/showpost.php?p=9911677&postcount=52) just in case someone gets mad for duplicates.

---

### Post by cariboo on 2010-10-01
Cross posting won't solve your problem, especially if you post the exactly the same thing in two different threads, it just creates a duplication of effort.

---

### Post by Terry32 on 2010-10-02
> **Ancanus said:**
> Forking from [this thread]("http://ubuntuforums.org/showthread.php?t=1572412") as it may not be the same issue.

While doing menial tasks (firefox, gedit,) my mouse clicking will suddenly stop working. I am still able to move the mouse cursor, and I am still able to operate the machine perfectly using the keyboard. It is just the mouse clicking that is affected.

To workaround this, I can shortcut a terminal open and do *sudo service gdm restart* and everything will be working until it occurs again.

How can I get the necessary information to bug-report this?

Check out this thread as it may be the same issue, [http://ubuntuforums.org/showthread.php?t=1585426](http://ubuntuforums.org/showthread.php?t=1585426)

Original poster had a Microsoft 600 Keyboard and I had a Microsoft 3000 keyboard, both which would would screw up the left mouse click if you do certain things with the keyboard. Seems that using the F keys or multimedia keys causes stuff to freak out until you unplug the keyboard and plug it back in.

---

### Post by NightwishFan on 2010-10-02
I have an issue where my mouse freezes. Switching virtual terminals and back fixes the issue. Does this workaround help with your problem? (Just asking to confirm if it might be a similar problem)

---

### Post by MishaAct on 2010-10-02
> **cariboo907 said:**
> Does anything show up in /var/log/messages and/or /var/log/kern.log?
This is the part of [https://bugs.launchpad.net/udev/+bug/637208](https://bugs.launchpad.net/udev/+bug/637208)

---

### Post by Terry32 on 2010-10-02
> **NightwishFan said:**
> I have an issue where my mouse freezes. Switching virtual terminals and back fixes the issue. Does this workaround help with your problem? (Just asking to confirm if it might be a similar problem)

Switching terminals does not fix my issue, both Microsoft Keyboards (600 and 3000) have the problem, my logitech works fine.

---

### Post by kmas on 2010-10-02
still haven't found a solution, i was trying to use easystroke to may be set my right click to ctrl click but that didn't work out too well.. 

i've tried to attach my kern.log bellow. also looked at the threads, suggested since my last post, and looked at the bugs as well, but don't seem to still find any solution..

---

### Post by Ancanus on 2010-10-04
> **MishaAct said:**
> This is the part of [https://bugs.launchpad.net/udev/+bug/637208](https://bugs.launchpad.net/udev/+bug/637208)

That is a bug report on A4Tech mouses. I don't know if it's a re-branding but my mouse is a Logitech MX518. I don't really switch keyboard layout either. This is probably a separate issue?

---

### Post by seahorsepip on 2010-10-04
I quess it has nonthing to do with mouse....(tested multiple mouses)
but I got problem with newest gedit and firefox...
so I fixed it by ussing ff 3.6.9 & gedit from main ppa of lucid!

---

### Post by Ancanus on 2010-10-04
> **seahorsepip said:**
> I quess it has nonthing to do with mouse....(tested multiple mouses)
but I got problem with newest gedit and firefox...
so I fixed it by ussing ff 3.6.9 & gedit from main ppa of lucid!

Now that you mention it, I recall always having firefox open when this happens. Perhaps the Firefox package is breaking a gtk object? I'll give the firefox ppa and report back if it occurs again.

---

### Post by Mr. Picklesworth on 2010-10-04
It's probably something grabbing the mouse, which leaves you at its mercy; there's no particular way to ungrab it. (My *favourite* part of X11!). This would be especially likely if you were doing any dragging / dropping or opening a menu,

Try switching to a virtual terminal and killing a few processes you have been using. Firefox would be my first guess. Each time, switch back and see if the mouse is working right. Consider filing a bug report against the offending application as it should let go of your mouse pointer properly.

You can also create a second pointer nowadays and attach a device to it (using the xinput command with list, create-master and reattach). That new pointer should work fine, free of any grabs.

---

### Post by Ancanus on 2010-10-05
> **Mr. Picklesworth said:**
> It's probably something grabbing the mouse, which leaves you at its mercy; there's no particular way to ungrab it. (My *favourite* part of X11!). This would be especially likely if you were doing any dragging / dropping or opening a menu,

Try switching to a virtual terminal and killing a few processes you have been using. Firefox would be my first guess. Each time, switch back and see if the mouse is working right. Consider filing a bug report against the offending application as it should let go of your mouse pointer properly.

You can also create a second pointer nowadays and attach a device to it (using the xinput command with list, create-master and reattach). That new pointer should work fine, free of any grabs.

Thank you, Mr. Picklesworth. I learned a new trick with xinput.
I will definitely give it a try and report back.

I'm curious, however. Would killing the application that has claimed the mouse pointer, cause the mouse pointer to be left unattached to anything?

---

### Post by Mr. Picklesworth on 2010-10-05
> **Ancanus said:**
> Thank you, Mr. Picklesworth. I learned a new trick with xinput.
I will definitely give it a try and report back.

I'm curious, however. Would killing the application that has claimed the mouse pointer, cause the mouse pointer to be left unattached to anything?

The grab is released automatically when the process exits, so the pointer (or keyboard) should work again.

---

### Post by Ancanus on 2010-10-08
> **Mr. Picklesworth said:**
> The grab is released automatically when the process exits, so the pointer (or keyboard) should work again.

Mr. Picklesworth,

killing Firefox and all user-started processes is not releasing the mouse. My current workaround is to use xinput to create a new master, and reattach my mouse to it.

Any idea on how to find the culprit?

Edit: Running xkill tells me that it is unable to grab my mouse. There must be some way to tell which application has hijacked the mouse...

---

