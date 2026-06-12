---
title: "ir-keytable doesn't work... my remotes are keyboards"
date: 2012-05-07
forum: Mythbuntu
---

### Post by alien878 on 2012-05-07
The mantis drivers have had IR support removed.  I have two USB IR receivers and I am trying to get one of them to work.

I found this useful post:

[http://forum.xbmc.org/showthread.php?tid=101151](http://forum.xbmc.org/showthread.php?tid=101151)

Unfortunately, ir-keytable doesn't work for either:

$ ir-keytable 
Couldn't find any node at /sys/class/rc/rc*.
$

Digging further, they are recognised as keyboards and I can see the keypresses with /lib/udev/keymap

The problem is, the default keymappings are completely useless.  While ir-keytable describes how to change the keymaps, it only works if the remote is recognised as a rc (ir-keytable works).

How do I change the keymappings for keyboards?  One remote is a twinhan and one is a formosa21.  I tried to use lirc anyway, but irrecord can't find them because " this device driver does not support the LIRC ioctl interface".

Thanks for any help.... I want to avoid purchasing yet more hardward and crossing my fingers and hoping it works.

Note: I'm using 12.04 (just upgraded from 10.11 as the mantis drivers are finally working for video)

---

### Post by alien878 on 2012-05-08
I think I may have found something:

[http://askubuntu.com/questions/69804/how-do-i-change-the-keymap-of-a-single-device-logitech-presenter](http://askubuntu.com/questions/69804/how-do-i-change-the-keymap-of-a-single-device-logitech-presenter)

I'll give it a try shortly.

---

### Post by alien878 on 2012-05-14
Okay... I wasn't able to use udev to change the keycodes because /lib/udev/keymap only displayed "unknown keycode".

However, /lib/udev/keymap did show the logical keynames (ex. PageUp, etc.) and I was able to use that to reprogram the keymappings in mythtv itself.

**I'm now lirc free! ** After cursing the document free kernal lirc, I now am very happy with it.

In summary, you need to (I'm skipping all the messy steps if your device isn't recognised... but that was never easy anyway):

1. Uninstall lirc and reboot.

2. Open an xterm and hit some keys on your remote to see if they appear as keypresses (if not, need to figure out why it wasn't recognised).

3. Go into the frontend setup and configure the keymappings that don't do what you want.  When entering the key, use your remote and the correct value will be filled in.

Hopefully, you're done.

If you can't get the keymappings to work because of conflicts, then you can try the following to remap them:

1. Run ir-keytable to see if it is recognised as an ir remote.

2. If it was recognised as a remote, run ir-keytable again and start pressing keys to see what keys are mapped to what buttons.  You can then try to remap them as described here (ignore the part about lirc... once they are remapped, you are done):

[http://forum.xbmc.org/showthread.php?tid=101151](http://forum.xbmc.org/showthread.php?tid=101151)

3. If it was not recognised as a remote, run sudo /lib/udev/keymap -i input/eventX (replace X with the device the remote registered... see /var/log/udev).  Now start pressing keys on the remote to see what keys are mapped to what buttons.  You can then try to remap them as described here:

[http://askubuntu.com/questions/69804/how-do-i-change-the-keymap-of-a-single-device-logitech-presenter](http://askubuntu.com/questions/69804/how-do-i-change-the-keymap-of-a-single-device-logitech-presenter)

4. If you don't like the default mappings and you can't or don't want to change the kernel mappings, you can re-install lirc and then do the mappings the old way.  I only recommend this as a last resort.

---

