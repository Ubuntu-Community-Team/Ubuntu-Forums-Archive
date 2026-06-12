---
title: "Alsa version not updated?"
date: 2011-04-29
forum: Multimedia Software
---

### Post by blup on 2011-04-29
Hello,

I have a bit of trouble with ALSA. I have the Realtek ALC892. Currently 5.1 sound is not working, it only gives me the option to use stereo in the audio menu. Apparently it should work with alsa 1.0.24, which should be in natty narwhal. I installed the last dev release before the offical version, so it should have updated it to this last alsa version. However this seems to have only affected the packages and not the kernel. Is that possible?

cat /proc/asound/version gives version 1.0.23, but the version of alsa-base, etc. is 1.0.24

How can I make sure that I have 1.0.24?

- blup

---

### Post by LxP on 2011-04-30
I am also having trouble with ALSA, so I have filed this as an Ubuntu bug:

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/774262](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/774262)

---

### Post by Yellow Pasque on 2011-04-30
This is expected behavior. /proc/asound shows the version of the kernel module built into the kernel, which is 1.0.23. If you want to build a 1.0.24 kernel module, use the ALSA upgrade script: [http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577)

---

### Post by LxP on 2011-05-01
> **Temüjin said:**
> This is expected behavior. /proc/asound shows the version of the kernel module built into the kernel, which is 1.0.23.

Step 3 of the Community Ubuntu Documentation's [Sound Troubleshooting Procedure]("https://help.ubuntu.com/community/SoundTroubleshooting") page states that the ALSA driver, library and utilities version numbers should all be equal.  In my case, they are all different:

```
!!ALSA Version
!!------------

Driver version:     1.0.23
Library version:    1.0.24.1
Utilities version:  1.0.24.2
```

To me this suggests a problem that shouldn't exist on a fresh Natty install.  Is this a correct assumption?

> **Temüjin said:**
> If you want to build a 1.0.24 kernel module, use the ALSA upgrade script: [http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577)

I appreciate the work you have put into this script, but introducing an inconsistency between what the packages think are installed and what's actually in place seems too risky for me.  Are updated packages likely to solve this problem in the near future?

Thank you for your assistance!

---

### Post by Yellow Pasque on 2011-05-01
> **LxP said:**
> Step 3 of the Community Ubuntu Documentation's [Sound Troubleshooting Procedure]("https://help.ubuntu.com/community/SoundTroubleshooting") page states that the ALSA driver, library and utilities version numbers should all be equal.
That may have been true of past Ubuntu releases, but Natty comes with 1.0.24.x user space and 1.0.23 kernel module. *shrug*

> To me this suggests a problem that shouldn't exist on a fresh Natty install.  Is this a correct assumption?
I don't think so. It's like that on all the fresh Natty installs, but I'm insterested to see what the devs have to say about it on the bug you filed.

> Are updated packages likely to solve this problem in the near future?
There may be backported alsa kernel modules after the next version of the linux kernel (2.6.39) is finalized, but there are none at the moment.

---

