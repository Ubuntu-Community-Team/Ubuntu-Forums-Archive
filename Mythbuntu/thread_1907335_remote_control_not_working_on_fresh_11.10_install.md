---
title: "remote control not working on fresh 11.10 install"
date: 2012-01-11
forum: Mythbuntu
---

### Post by Errorsmith on 2012-01-11
Hi
I just did a fresh Install of Mythbuntu 11.10. I am using two hauppauge hvr1300 configured for dvbt. Additionally i have installed an old hauppauge wintv pci fm card, wich i intend to use for the remote control only. Unfortunately this doesnt work out as expected. Apparently lirc doesnt even start. When starting it from the commandline, it complains about a missing /dev/lirc. Can anyone point me into the right direction to solve this issue?

With kind regards,
Errorsmith

---

### Post by Phyrewire on 2012-01-23
I have a similar problem.  My remote was working with Mandiva and Myth installed.  After installing 11.10 it doesn't work.

irw doesn't show anything
ir-keytable -t -d /dev/input/event6 will show when a button is pressed.

What can I try or look at?

---

### Post by wyliecoyoteuk on 2012-01-31
I managed to fix my remote in Mythbuntu by configuring as a keyboard, bypassing all of the LIRC stuf
[http://wyliecoyoteuk.wordpress.com/2012/01/30/how-to-forget-lirc-for-mythtv-remotes/](http://wyliecoyoteuk.wordpress.com/2012/01/30/how-to-forget-lirc-for-mythtv-remotes/)

---

### Post by wyliecoyoteuk on 2012-02-02
> **wyliecoyoteuk said:**
> i managed to fix my remote in mythbuntu by configuring as a keyboard, bypassing all of the lirc stuff. Lirc drivers are now in the kernel, so lirc does not even need to be installed for this method to work.

[http://wyliecoyoteuk.wordpress.com/2012/01/30/how-to-forget-lirc-for-mythtv-remotes/](http://wyliecoyoteuk.wordpress.com/2012/01/30/how-to-forget-lirc-for-mythtv-remotes/)

oops, hit quote instead of edit

---

