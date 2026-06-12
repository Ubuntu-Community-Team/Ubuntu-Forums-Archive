---
title: "Printing to a Windows 7 printer from Ubuntu"
date: 2010-05-11
forum: Networking &amp; Wireless
---

### Post by goatgonads on 2010-05-11
I have been tirelessly attempting to print from my ubuntu machine to my windows 7 machine, to no avail. 

I have tried following the guide:
[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

When I click (in Ubuntu) add "network printer via samba" and enter in the ip address of the PC "192.168.1.101", it pops up a browser showing the computer. I then click the dropdown menu next to the PC, and I am prompted for a password. I enter in the W7 homegroup password, and it tells me that the password is incorrect.

I have enabled file and printer sharing on the W7 box, and removed the wndows live ID assistant program.

Any further suggestions would be greatly appreciated.

---

### Post by goatgonads on 2010-05-12
anyone?

---

### Post by homburg on 2010-05-13
I have succeded in connecting to my windows 7 shared printer, but I am still not printing...

My windows 7 settings:

Uninstalled Windows Live ID assistant
"share printers" -> Enable 40-,56-bit encryption

Ubuntu printer install:
"Printing" -> "Add" -> "Windows printer..." -> "Set authentication details now" (i enter the password for my login on the windows 7 machine)

Now the print jobs are appearing in the Windows 7 printing queue as "remote backwards compatible job...".
But the jobs are never printed...

(I have translated most of the UI text menu names from danish, so the actuelt english UI may have different wording)

---

### Post by homburg on 2010-05-13
also, I have installed samba from lucid-proposed
[https://wiki.ubuntu.com/Testing/EnableProposed](https://wiki.ubuntu.com/Testing/EnableProposed)

---

### Post by adelricbilly on 2010-05-13
Yes, both HP and Brother are easier to set up in ubuntu than Windows.  I tried installing the HP Windows software, then receiving a new install CD, I never did get it to scan. it found the HP, installed the drivers, and it worked. For interested folks, Windows 7 is working very well for me on a 3-yr-old system Pentium D with 1 gig ram.  I am even using the x64 version.

---

