---
title: "Dell Vostro 1000 vertical lines in video - sometimes"
date: 2010-08-30
forum: Multimedia Software
---

### Post by Scott. on 2010-08-30
Newbie to Linux not to computing. - I loaded Ubuntu 10.10 beta (I had the same problem with 10.04). Everything works after the install, even for another boot. After this right in the middle of the Ubuntu screen with the little red dots, all I get is colored vertical lines. (I think the audio may be out too). I'm having trouble figuring this out because it's consitently inconsistent. Any ideas would be appreciated. (Please remember I used to to program interrupts for drivers under DOS but don't know what the hell I'm doing in Linux. Besides, I can't get to a command prompt.) - Thanks Scott

---

### Post by apfejes on 2010-09-19
The Vostro 1000 is strange.  I get these evey time I shut down, and occasionally when you start up.

The trick to avoiding them on the start up (so that you can get into X and then gdm/kdm) is to append "radeon.modeset=0" to the boot line (right after quiet splash) in the boot menu.  I typically end up adding this to the /etc/default/config file (again, right after "quiet splash", which then applies it automatically.

---

