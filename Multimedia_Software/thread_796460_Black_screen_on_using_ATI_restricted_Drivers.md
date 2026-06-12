---
title: "Black screen on using ATI restricted Drivers"
date: 2008-05-16
forum: Multimedia Software
---

### Post by notmentat on 2008-05-16
Hi All, 
I installed Hardy Heron last night, got everything up and running fine.
I then opted to install the restricted drivers as the notification suggested on the menu bar.
When I rebooted I get all the text flying up the screen as usual, but then the screen just goes black and nothing more happens.

I know very little about getting stuff working in linux, so I'm completely clueless about how i would go about getting rid of the restricted drivers so I can boot as normal.
I'm using an ATI X800XL if that makes any difference.

Thanks.

---

### Post by megadave on 2008-05-17
I had/have the same problem.

Temporary solution until someone smarter than me comes up with a fix is to revert back to the original driver.

Step 1:  reboot
Step 2:  choose the safe/repair mode
                within that choose the repair x server option
Step 3:  choose continue booting normally
Step 4:  Login, White screen of death appears
Step 5:  Ctrl-Alt-Backspace to kill the x-server
Step 6:  at the login screen under the options choose gnome failsafe
Step 7:  navigate thru system-admin-hardware drivers and untick the
         restricted driver.
Step 8:  Reboot
Step 9:  At login, under options choose Gnome (not the failsafe).
Step 10:  You're back where u started.

:guitar:

---

