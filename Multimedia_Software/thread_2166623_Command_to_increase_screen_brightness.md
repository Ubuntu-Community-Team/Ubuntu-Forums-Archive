---
title: "Command to increase screen brightness?"
date: 2013-08-10
forum: Multimedia Software
---

### Post by AnotherKevin on 2013-08-10
I need to increase the brightness in my screen.  I have an HP Omni 100 PC.  It's a dual core with 3 gigs of RAM.  It came with Windows 7, which I dumped for Ubuntu (current version).  All of the "built-in" controls don't work without Windows, including screen brightness.  In the System Settings, I have only resolution, etc., which I can adjust.  No options I could find to increase the brightness.

I'm no noob to Ubuntu, but I haven't used Ubuntu for a couple of years.  Was hoping to find a terminal command or something along those lines.  Can any one help?

Thanks!
Another Kevin

---

### Post by gordintoronto on 2013-08-10
What is the video adapter? Have you installed an "additional driver"?

---

### Post by Rob Sayer on 2013-08-11
Try this to find out what adapter & driver, esp. the first answer:

[http://askubuntu.com/questions/23238/how-can-i-find-what-video-driver-is-in-use-on-my-system](http://askubuntu.com/questions/23238/how-can-i-find-what-video-driver-is-in-use-on-my-system)

I've done this on a couple of machines, and it wasn't complicated.  I just edited the grub config file and then (important) run sudo update-grub.  Not knowing the video adapter I don't want to specify the exact command I used, but it should be quite easy to find.

---

