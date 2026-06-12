---
title: "Computer won't boot with new wireless card"
date: 2009-12-29
forum: Networking &amp; Wireless
---

### Post by odsus1 on 2009-12-29
I have a sony vaio PCV-2234 running Karmic. 
I re-arranged my network to accommodate a media computer (Ubuntu Studio rocks) so I put a new wireless card in my karmic machine, now it will not boot, i tried recovery mode and booting to jaunty to no avail, if I remove the card it works just fine. The wireless card is a belkin f5d7000 pci card, thanks for any input. 

Odie

---

### Post by hotstovejer on 2009-12-29
Have you tried putting the card into another slot on the motherboard?

Thanks!

Jeremy

---

### Post by odsus1 on 2009-12-29
yes, i put it into all three of my pci slots.

---

### Post by mdmarmer on 2009-12-29
Try booting with acpi=off

---

### Post by odsus1 on 2009-12-29
is that in the bios? if it is I can't find it.

---

### Post by mdmarmer on 2009-12-29
No, that's a boot cheatcode.  You add it to the boot options on your kernel boot line.  Usually on the grub screen you can just type acpi=off where the cursor is when the screen comes up, or press <ESC> and then <ENTER> to get an editable boot screen, then use the arrow key and e to select the right boot sequence, then arrow and e to select the kernel boot line, then add acpi=off to the end of the line.

[https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation](https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation)
(See #4 -- the url didn't select the proper section of the help)

Mike

---

### Post by odsus1 on 2009-12-29
no dice.

---

### Post by mdmarmer on 2009-12-29
Tell us more about what happens when u try to boot. Does the computer get so far and then freeze?  Usually there is some key combination to watch the boot messages, like <alt> <F1> or <ctrl> <alt> <F1>

---

### Post by odsus1 on 2009-12-29
the computer boots normally, shows the ubuntu logo (the static one not the fancy new splash screen) and then goes to black and freezes.

---

### Post by mdmarmer on 2009-12-29
Like I said, u need to break out of that screen so you can look at the messages.  Sometimes networkmanager or a driver can cause a freeze, and you can fix this by removing networkmanager or using the blacklist to tell the driver not to load.

I don't run Ubuntu so it's hard for me to get specific about keys, programs and drivers, but I have experienced and fixed lots of freezes on boot.

---

### Post by odsus1 on 2009-12-29
Going into recovery mode i was able to see some errors, they look to be video related though, here they are:

[     1.987426] render error detected, EIR: 0x0000000x10
[     1.987431] [drm:i915_handle_error] *ERROR* EIR stuck: 0x0000000x10, masking
[     1.987439] render error detected, EIR: 0x0000000x10

I have to copy all of this by hand so if you need more it will take me a few min to enter it all.

---

