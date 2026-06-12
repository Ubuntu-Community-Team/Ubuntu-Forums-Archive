---
title: "Big Trouble"
date: 2009-12-19
forum: Networking &amp; Wireless
---

### Post by cheesefry on 2009-12-19
Having problems with my wireless. Looked thru the threads and cannot find any to resolve. I have a Gateway LT20 and am under the assumption that the Acer AOD250 is basicly the same, so I have been searching for the acer model. Anyway, went down thru the Synaptic PM and repository, etc... tried all that. The wireless is BCM4312 (Broadcom Corp).

 I rebooted my computer and now I have nothing but a black screen. If I hit F2 idurring boot, it installs Grub and gives me a few options. (boot generic, boot generic recovery, test memory) If I boot generic, it brings me to the blank screen and that is all. Can't do anything, type anything etc.. If I boot recovery it allows me to log in, but then waits for a command. I don't know enough to give it a command. Any suggestions??

---

### Post by yelvington on 2009-12-19
This doesn't sound like it has anything to do with wireless. You're booting into a black screen? What did you do before rebooting? 

At any rate, don't panic. The worst case scenario is that you have to reinstall Ubuntu, in which case you can boot from USB and back up your user data first.

---

### Post by cpplinux on 2009-12-19
Can you get a console by pressing Ctrl-Alt-F1/F2/F7? If so, login and check the boot logs.

---

### Post by Roliat on 2009-12-20
I have a very similar problem here: HP2133 with BCM4312, Karmic 2.6.31-17 (x86_32). Activating STA driver works like a charm until next reboot, then an evil blackscreen appears. This happens again and again until I decide to boot into 2.6.31-14 and deactivate the STA driver there. So I think this really is wireless-related somehow...

---

