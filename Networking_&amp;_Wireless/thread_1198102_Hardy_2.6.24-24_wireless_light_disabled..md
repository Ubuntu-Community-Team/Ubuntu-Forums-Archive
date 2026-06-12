---
title: "Hardy 2.6.24-24 wireless light disabled."
date: 2009-06-27
forum: Networking &amp; Wireless
---

### Post by pgmer6809 on 2009-06-27
Hi,
Running hardy on an HP laptop with intel 3945ABG internal wireless card.
Recently did a bunch of updates;
Under Hardy kernel 2.6.22-26-generic (which I can still boot) the LED which shows if the wireless txmitter is enabled or not worked fine.
Under Hardy kernel 2.6.24-24-generic the light does not work.
The network works fine, in fact I am using it as I type, but I am now never sure if the 'wireless killswitch' has been pushed by accident or not.
Is there a fix for this?
I notice that under the hardware menu in the taskbar there is a device which is the 'killswitch', maybe the led is tied to that? maybe there is a file that needs editing to enable Linux to allow the LED to become active?
(It normally blinks furiously when in use, or intermittently when trying to connect).
PS
the dmesg, lshw -C network, iwconfig etc cmds all look normal, as you would expect with a working interface.

pgmer6809

---

### Post by bakermiller on 2009-07-15
I just installed kernel 2.6.24-24 on aspire one. I had tried a few months ago giving me kernel panic, so i commented out this kernel in /boot/grub/menu.lst. 

This time it out worked fine. I did not even have to recompile ALSA for sound.

only, at the first reboot, i had a dev.wifi0.ledpin error. I recompiled the madwifi drivers and rebooted. The led is now blinking.:guitar:

---

