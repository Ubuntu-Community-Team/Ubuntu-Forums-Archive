---
title: "Power Management Warning on 1st boot!"
date: 2010-07-26
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by kevpan815 on 2010-07-26
I am back and I successfully installed Maverick Alpha 2 on my backup home computer earlier today, however on first boot I got a Power Management error problem! Has anyone else had this problem? Please Note that I will most likely be unable 2 file a Bug Report 4 this issue, if my dad catches me connecting Linux 2 his ISP, he will take my Internet Access away from me, just fyi.

---

### Post by Sam on 2010-07-27
Well it happen once for me, but after an upgrade. All I did is```
sudo apt-get install --reinstall gnome-power-manager
``` and rebooted. Problem was fixed. I hope it will be the same for you.

---

### Post by x-shaney-x on 2010-07-27
Seems to be more than one power management issue there ;)
Do you have a particular error you can post.
I wouldn't think gnome-power-manager would give out errors on boot?

---

### Post by kevpan815 on 2010-07-27
It said that the Power Management System is still running!

---

### Post by kevpan815 on 2010-07-27
I am unable 2 attempt 2 install updates right now due 2 the fact that the computer is offering me a Partial Upgrade right now. I did try the  Power Management Reinstall with out installing Updates and it did not fix the problem.

---

### Post by kevpan815 on 2010-07-30
Issue Solved. Since the Update-manager was still offering me a a Partial Upgrade when I logged in this morning, I went ahead and installed all the regular updates first, Rebooted, and then installed the Partial Upgrade second, Rebooted a Second Time, and then finally I Reinstalled Gnome-Power-Manager using the process listed by the previous poster.

---

