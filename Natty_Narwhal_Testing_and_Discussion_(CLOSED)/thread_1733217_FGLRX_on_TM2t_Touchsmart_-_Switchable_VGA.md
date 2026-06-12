---
title: "FGLRX on TM2t Touchsmart - Switchable VGA"
date: 2011-04-19
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by tembares on 2011-04-19
Hello,
Thank you for reading my post.

I have a HP TM2t Touchsmart 2100 CTO. There is an Intel and ATI HD 5450 graphic card inside.

(I cannot find it anymore where I got it from, but) I found a script on the internet about switching between the graphic cards. The script works, only it turns off the I915 Intel card, but does not turn on the ATI card. I come in a text-mode with the Linux messages (time: message, like dmesg).

Reason why it does not turn on the ATI card is that the drivers were not activated (prop. driver not installed).

But after installing the FGLRX driver, I only get a black screen.

To start Ubuntu Natty I added 'xforcevesa' in GRUB. This makes the graphical interface working for me. Can this be a cause?

Who can help me to get it work. I read on the internet that someone said it worked for him.

I am working now with Ubuntu Natty Beta 2.

Thank you in advance.

---

### Post by Mark Phelps on 2011-04-19
Ubuntu 11.04 is still in testing.  This thread is reserved for Ubuntu versions that have already been released.  You should be posting your 11.04 questions to the Natty Development forum.

Had you gone there first, you would have discovered that there are problems in the Betas with the AMD restricted drivers.

Suggest you go to that forum and check out the threads.

---

### Post by s.fox on 2011-04-19
Thread moved to Natty Narwhal Testing and Discussion

---

