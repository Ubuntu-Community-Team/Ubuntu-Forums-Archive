---
title: "oops"
date: 2009-10-11
forum: Mythbuntu
---

### Post by benlyboy on 2009-10-11
I screwed up :)

Late last night I was playing with the setting just seeing how things worked. I changed the setting in appearance for the GUI, and now when ever the front end loads my monitor tells me that it is out of range and turns off.

So is there a way to reset these setting with out starting the front?



thanks

---

### Post by lncoll on 2009-10-11
Is quite simple, boot in the second grub option, "Recovery mode", after boot you ge a menu, select "Reconfigure X server".

---

### Post by benlyboy on 2009-10-11
OK sounds good, but how do you get into Recovery mode?

---

### Post by lncoll on 2009-10-11
> **benlyboy said:**
> OK sounds good, but how do you get into Recovery mode?

Simple, boot or reboot your PC, at boot you'll get a screen where select the kernel or OS to boot, if not you'll get a prompt that says "press ESC for the menu" or similar.
In this menu, there are some options, the first uses to be the default option (Ubuntu 9.04, kernel 2.6.28-15-generic), the second one is the one you must select (Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)) to reconfigure your X server.

---

### Post by benlyboy on 2009-10-11
ok thanks for the help in getting into the recovery menu

But where to from there?

the menu options are
 
resume normal boot
try to make free space
repair broken packages 
update grub boot loader
drop to root shell prompt with networking

thanks again for the help

one other thing I'm not sure it is x server I need to reconfigured. Its the front end that needs setting up. If I close the myth front end after booting the screen works fine but as soon as I restart the front end the screen tells me that the setting our out of rang and closes down

---

