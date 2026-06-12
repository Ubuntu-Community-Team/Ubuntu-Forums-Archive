---
title: "No Battery issue In TOSHIBA laptop"
date: 2011-05-13
forum: Multimedia Software
---

### Post by thuci on 2011-05-13
I use toshiba satellite L655 laptop, I recently installed Ubuntu10.10.In gnome power manger ther is no tap for 'On Battery'. When I run this command 
 dmesg | grep batt
it returns as
[    0.752856] ACPI: Battery Slot [BAT1] (battery absent)
Please anyone help to solve this!

---

### Post by varunendra on 2011-05-13
> **thuci said:**
> 
[    0.752856] ACPI: Battery Slot [BAT1] (battery absent)
Please anyone help to solve this!
Do you have the battery properly installed in its slot? What happens when you boot Ubuntu on batteries?

---

### Post by thuci on 2011-06-23
when boot ubuntu on batteries power indicator always indicates as AC power plugged in

---

### Post by Blasphemist on 2011-06-23
This may sound too simple but please give it a try. Shut down, unplug the AC, take out the battery and hold the power button down for at least 30 seconds. Then re-insert the battery, plug in the AC and reboot. See if that changes it.

---

### Post by dirkoid on 2011-07-02
Hi,

I had the same issue on my L655 S5168 with Maverick (different model though) and found this solution worked.

[http://techinterplay.com/fix-toshiba-battery-issue-linux.html](http://techinterplay.com/fix-toshiba-battery-issue-linux.html)

Seems there are two versions of boot info, Windows reads the correct one and Linux does not. The fix involves correcting and recompiling the table and compiling into a new kernel.

Sounds a lot worse than it is. The instructions are very complete and easy to follow and when you're done you have a new kernel package installed in the grub menu.

As always YMMV but if you're comfortable it is certainly worth a try.

Cheers

---

