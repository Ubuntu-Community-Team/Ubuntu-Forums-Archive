---
title: "Samba shares become unshared after reboot"
date: 2009-08-27
forum: Networking &amp; Wireless
---

### Post by thecompnerd on 2009-08-27
I'm trying to share out two data hard drives in this computer via Samba.  I'll go to the properties of the drive, share it and enable guest access.  I'll go to my Windows box to make sure the share works, which it does.  Then, I'll reboot the server and log back in as the user I created the shares under and it's been unshared.  I can only get the shares to stay if I'm logged in as root and create them, but then I have to always log in as root which I don't want.

I have a feeling it has something to do with the fact that I'm automounting the 2 data drives with pysdm at bootup.  It seems as though the share is being stripped as the drive has to be remounted?

Thanks.

I'm on 9.04, BTW.

---

### Post by Iowan on 2009-08-27
**dmizer** has a couple of How-To's on Windows/Samba sharing:
[http://ubuntuforums.org/showthread.php?t=1169149]("http://ubuntuforums.org/showthread.php?t=1169149")9
[http://ubuntuforums.org/showthread.php?t=288534]("http://ubuntuforums.org/showthread.php?t=288534")

---

### Post by thecompnerd on 2009-08-28
Neither thread appears to answer my question.

My issue is that the Ubuntu server I'm running has two shares on it, on two separate internal hard drives that are becoming unshared after reboot.  Thus, I have to continue to reshare those folders after reboot so that my Windows box can see them.  This is not a case of trying to permanently mount Windows remote shares on my Ubuntu box like the other threads were addressing.

---

### Post by Iowan on 2009-08-28
Sorry...
I was hoping some of the "mounting" information would be helpful.  I'll try to do some research on **pysdm**.

---

### Post by thecompnerd on 2009-08-28
I may have found a bug...

It turns out that the share is being created and maintained after reboot, it just appears as though the folder is no longer shared after going to the share tab, "share this folder" is no longer checked.  I verified that the shares are available from a windows box.

---

### Post by lunatico on 2009-10-08
> **thecompnerd said:**
> I may have found a bug...

It turns out that the share is being created and maintained after reboot, it just appears as though the folder is no longer shared after going to the share tab, "share this folder" is no longer checked.  I verified that the shares are available from a windows box.

I was looking for a solution to this as I thought my shares where disappearing after reboot... I read this and couldn't believe it. Rebooted my Ubuntu machine with the shares and even before login the share available. The folder shows normal (no share icon) and in properties the share option is not selected.

Definitively a bug!

Anyone reported this to launchpad?

---

