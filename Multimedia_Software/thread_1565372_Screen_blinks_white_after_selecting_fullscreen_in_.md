---
title: "Screen blinks white after selecting fullscreen in a Flash video"
date: 2010-08-31
forum: Multimedia Software
---

### Post by benny7440 on 2010-08-31
As the title implies I can't use the fullscreen feature in a flash video because all the screen turns white &, wherever the pointer was, get noticed as a faint shadow. I can increase the screen only if using the keyboard shortcut <Ctl++> keys combination.
Have Shockwave Flash 10.1.r82 add-on. Firefox version is 3.6.8. Ubuntu = 10.0.4 LTS.
Thanks for any advice!

---

### Post by lovinglinux on 2010-09-01
See the third item at [Flash Issues & Solutions](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html).

Let me know if it works for you.

---

### Post by benny7440 on 2010-09-24
Thanks for responding lovinglinux! Had problems with the last command in your referenced page:[sudo mv ~/mms.cfg /etc/adobe/]. I'll close the browser & the terminal window and then open FF back & try to run the said command to see if that works. If not, then I'll reboot the whole system & try it again. If none of the above approaches work then, what should I do with the outcome of the first 2 commands?

---

### Post by lovinglinux on 2010-09-24
> **benny7440 said:**
> Thanks for responding lovinglinux! Had problems with the last command in your referenced page:[sudo mv ~/mms.cfg /etc/adobe/]. I'll close the browser & the terminal window and then open FF back & try to run the said command to see if that works. If not, then I'll reboot the whole system & try it again. If none of the above approaches work then, what should I do with the outcome of the first 2 commands?

You must have typed something wrong because there is no reason for it to fail. You don't need to do anything if it fails again, but you could simply delete the created files.

The first command creates a folder named adobe in /etc, the second creates a file named mms.cfg in your /home and the third moves it to the /etc/adobe folder.

---

