---
title: "nvidia geforce 8400GS ubuntu 7.10"
date: 2008-06-27
forum: Multimedia Software
---

### Post by stmartin on 2008-06-27
Hello!

I have huge problem with the drivers of the 8 Series. First, I downloaded them from the official site of NVIDIA. I downloaded the NVIDIA-Linux-x86-173.14.09.pkg1.run package, and installed it properly with no problems. The only problem is when I restart the computer. On every log-on I received error message, that my graphic card is not properly detected, and that I should configure it manually. There are buttons Configure... Apply.. etc..

Thank you. I expect answer as soon as possible.

---

### Post by leviphyl on 2008-06-27
As you seem to be out of luck with others..

I don't know the level of your expertise, but if you hadn't done so yet, check your dmesg and X log. If you are unfamiliar with them, show them, somebody surely understands it...

---

### Post by Pjotr123 on 2008-06-27
You shouldn't have downloaded anything manually.

Do this:

1. Repair your graphical environment. It's 7.10, so you have to use the old way:
in the terminal: sudo dpkg-reconfigure xserver-xorg

Agree to every proposed answer. Use the following keys: Tab, Space bar, arrows, Enter.

2. Install the restricted driver the easy way:
[http://ubuntutip.googlepages.com/thefirstthingstodo](http://ubuntutip.googlepages.com/thefirstthingstodo)
(number 2 )

---

### Post by stmartin on 2008-06-28
Thanks, but it didn't helped. When I first installed the drivers I went to Applications/System Tools/NVIDIA X Server Settings and I pressed Save Configuration File. It didn't work. Seems like I need to be logged as root all the time to save the configuration file. On the end of the installation, it asked me something like "Do you want to do 'nvidia-xconfig' on every start so you can use the drivers installed? " I tried with both "Yes" and "No" and again the same problem.

---

