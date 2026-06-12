---
title: "No display after video card upgrade"
date: 2009-04-04
forum: Multimedia Software
---

### Post by Stolea on 2009-04-04
Hi all,
I had to replace my ATI Raedon 9600XT card due to its untimely demise. The replacement card was an ATI X-1650-512mb card. After installation, Ubuntu starts the normal way, but then sits with a black screen.
I assume that is caused by the ATI driver. How do I get my screen to work? Any ideas.

---

### Post by Stolea on 2009-04-04
Anyone, please.

---

### Post by axelroo on 2009-04-04
First thing is first. You need to be able to get to some kind of prompt. Reboot and when GRUB loads, hit ESC. You will have a menu to start Ubuntu in recovery mode; do it.  After it loads, you'll have a utility menu. One of the options is to attempt to repair Xorg's video., Try that first.  If that doesn't work, there is also an option to run a terminal w/ networking. From there you can uninstall and reinstall the ATi drivers. Let me know how the first option goes.

---

### Post by Stolea on 2009-04-04
Thanks, I will try that this evening.
Cheers

---

