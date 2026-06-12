---
title: "couple of questions"
date: 2009-07-24
forum: Networking &amp; Wireless
---

### Post by rahulsingh.nitrkl on 2009-07-24
Hi, everyone please help me with these.
Need to know a few things.  I have used **unetbootin-windows-356** to run live sessions on a usb drive.

1) Are changes made during live sessions saved on the pen drive?

2)  I am trying to spoof my mac address but it says access denied. Is it possible to change mac addresses during live sessions. if yes how? A friend of mine has told that i need to have access to "root" to change mac address and this is not possible during live sessions. If it is not possible, how do i change mac address if i have installed ubuntu on my harddisk.

please try to explain in simple terms as i am new to ubuntu and have failed to understand some of the solutions i found on internet. Thanks a lot.

---

### Post by ajgreeny on 2009-07-24
Just use **sudo** in front of the command or **gksudo appname** to open a gui application, and even though there is no password needed, I think you still get root privileges in the live CD session.  Try it, and apologies if I'm wrong.

---

### Post by martinbaselier on 2009-07-24
It all depends on the distro. In ubuntu you can use sudo without a passwords. In some other distros you would need su. If there's a password you can usually find it in the documentation.

sudo you'd use in front of a command, or gksudo if you prefer to type your password in a window. su is used to switch user, without any options, you'll switch to root. You would need to be root to be allowed to change the mac address.

---

### Post by rahulsingh.nitrkl on 2009-07-25
Thanks, it worked. I was able to change my mac address.

---

