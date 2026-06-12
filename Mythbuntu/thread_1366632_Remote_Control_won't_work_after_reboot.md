---
title: "Remote Control won't work after reboot"
date: 2009-12-28
forum: Mythbuntu
---

### Post by Zeedok on 2009-12-28
I am running Mythbuntu 9.10 (upgraded from 9.04 where the remote was working perfectly) with a MCE remote.  Every time I reboot my HTPC (which is thankfully not often) my remote control stops working.  I have found that if I uninstall and reinstall LIRC via the Mythbuntu control centre, the remote works again.  I have also noticed that when installing LIRC I have to enter my password 2 or 3 times (ie one of the packages must be installed as root).

I don't know what is causing this problem, but I wonder if it is an issue with permissions (ie the config is not being saved from one session to another) because I have also have had permissions problems when trying to delete recordings ([see this thread]("http://ubuntuforums.org/showthread.php?t=1363722")).

Has anyone else encountered this one?  Can someone suggest a solution?

Thanks

---

### Post by Zeedok on 2010-01-02
This problem has persisted, despite a clean reinstall.

I had some suggestions on what the cause may be from another forum site - essentially I think I have multiple lirc devices on the system.  My HTPC case came with an inbuilt remote control system which I am not using.  The user suggested that I create a udev rule to make sure the correct device is being chosen, but did not give any instruction as to how.

Can anyone walk me through it??

Thanks

EDIT [Found this thread which looks promising.]("http://ubuntuforums.org/showthread.php?t=168221")

---

