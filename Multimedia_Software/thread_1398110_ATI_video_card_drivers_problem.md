---
title: "ATI video card drivers problem"
date: 2010-02-04
forum: Multimedia Software
---

### Post by CrazySat on 2010-02-04
Hi all,

I am a begineer with Linux systems.

I am using Ubuntu 8.04 LTS and I recently installed drivers for my ATI Radeon HD 2400 PRO AGP video card (ati-driver-installer-10-1-x86.x86_64.run)
I could the finally enable visua effects with "Normal" selection.
When I switched at Grub boot from used kernel 2.6.24-26 to previous kernel version 2.6.24-25, I had to reinstall video drivers since scroll of all windows, indluding Firefox ones, was in slow motion.
When I came back to kernel 2.6.24-26 I had again same problem and I had to install once again video card drivers by running ati-driver-installer-10-1-x86.x86_64.run

Is it normality that I have to reinstall all the times ati-driver-installer-10-1-x86.x86_64.run video drivers? Or is maybe in my install anything going wrong ?

Thank you for your help.

---

### Post by overdrank on 2010-02-04
Hi and I believe the answer is yes if you manually install the drivers. If you use the restricted drivers then no.
Moved to Multimedia & Video

---

### Post by CrazySat on 2010-02-04
Thank you for your answer, overdrank.

I do apologize if I posted in wrong section ...[[COLOR=#D40000]****[/COLOR]]("http://ubuntuforums.org/member.php?u=234741")

---

### Post by markbuntu on 2010-02-04
The driver includes kernel modules and these need to be installed in each kernel but once installed they should not need to be reinstalled if you switch to another kernel and then back.  I use generic and rt kernels on 8.04 and switch between them and I have not seen this problem myself.

---

### Post by CrazySat on 2010-02-05
Thanks markbuntu,

Whenever I switch from one kernel to another kernel I have also to set again "Normal" visual effect and in Compix 4 desktops and Cube options as well. That's very odd.

---

