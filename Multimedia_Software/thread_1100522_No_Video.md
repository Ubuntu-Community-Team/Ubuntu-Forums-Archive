---
title: "No Video"
date: 2009-03-19
forum: Multimedia Software
---

### Post by wbee on 2009-03-19
Hello,

When prompted,I downloaded the recommended nvidia proprietary driver. It took forever to load,but it DID improve my video.

The next time I booted up,the screen took my name and password properly,but I got a notice that the frequency was outside a range that my monitor could process. (plain vanilla LCD monitor,set at 60hz) All I had was a black screen with the above notice.

I had to do an "unplug",which I don't like doing,but the same thing happened again.

Is there a solution short of a reinstall? Even with a reinstall,is there something to do if it happens again with the fresh install?

------------

Thank you.

---

### Post by norwoods on 2009-03-19
when you boot up, press the Esc key when grub says Press 'Esc' to enter the menu
then press the down arrow to highlight the menu entry ending with (recovery mode)
press Enter
you should get the Recovery Menu
repeat pressing the down arrow to highlight the menu entry: 
root Drop to root shell prompt
type nvidia-xconfig
press Enter
wait for prompt
reboot

or try the menu Recovery Menu entry:
xfix Try to fix the X server
but this will probably get rid of the proprietary driver.

---

### Post by wbee on 2009-03-19
norwoods,

Thank you.

---

