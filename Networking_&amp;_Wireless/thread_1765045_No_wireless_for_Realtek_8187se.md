---
title: "No wireless for Realtek 8187se"
date: 2011-05-22
forum: Networking &amp; Wireless
---

### Post by adamgreen on 2011-05-22
well, i'm new to ubuntu and linux and i'm having troubles with setting my wireless driver on ubuntu 11.04

i've searched around the and found many tutorials but none helped

this is the closest i ever got to a solution:
i found this [http://linuxwireless.org/en/users/Drivers/rtl8187](http://linuxwireless.org/en/users/Drivers/rtl8187)
which led me to these drivers [http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=tree;f=drivers/staging/rtl8187se](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=tree;f=drivers/staging/rtl8187se)
but i have no ideia how to make it work


please, help
and thanks!

---

### Post by ajgreeny on 2011-05-22
We need to know what hardware so in terminal run ```
sudo lshw -C network
``` in terminal and copy the output back here.

The output from ```
lspci | grep Ethernet
``` may also be useful.

EDIT:  Sorry, I missed your thread title with the hardware shown.

It looks as if this card is a bit of a problem, though there may be some help in the first post of [http://ubuntuforums.org/showthread.php?t=1103839](http://ubuntuforums.org/showthread.php?t=1103839)

---

### Post by sanderj on 2011-05-22
What exactly is the problem? For example: do you see any WLANs via the 'pie-chart' / rainbow icon in the upper right corner in Ubuntu?

What happens when you select: System -> Administration -> Additional Drivers?

---

### Post by adamgreen on 2011-05-22
> **sanderj said:**
> What exactly is the problem? For example: do you see any WLANs via the 'pie-chart' / rainbow icon in the upper right corner in Ubuntu?

What happens when you select: System -> Administration -> Additional Drivers?
No, there are no WLANs on the 'pie-chart' and the Additional Drivers shows nothing...

PS: Before installing (using Ubuntu via pendrive) it was working perfectly...

---

### Post by adamgreen on 2011-05-22
Guys, I have a question

If the wireless worked on the Live CD (before installing) isn't there a way to use that driver on the installed version? 

It sounds too weird that it doesn't work now...

---

### Post by sanderj on 2011-05-23
> **adamgreen said:**
> Guys, I have a question

If the wireless worked on the Live CD (before installing) isn't there a way to use that driver on the installed version? 

It sounds too weird that it doesn't work now...

Yes, that's weird. You could boot the Live CD again, check that wireless works again (with or without installing additional drivers), and look up which driver is used (dmesg and/or lsmod). You can do that using this command:

```

hwinfo --network
```

Search for the WLAN part and see which driver is used.

---

