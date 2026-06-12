---
title: "must run LIGHTDM to get login screen"
date: 2012-05-01
forum: Multimedia Software
---

### Post by cvc505 on 2012-05-01
This may be a duplicate but I have not found a solution as  yet: When I boot the computer, only the bottom half of the login screen is  displayed on the top portion of the computer screen. Dragging the mouse  around the screen causes artifacts to be displayed. I am able to log in  but still only see the bottom half of the display shown on the top half  of the screen.


  computer: Acer Asprie AO751 

OS: Ubuntu 12.4 LTS
 Video: Intel system controller hub (schpoulson) graphics controller 

Video driver in use: GMA 500 

Grub: "...i915.modeset=1 quiet splash acpi=force"


  If I log in then logout and back in immediately, I will get the full  screen display as I should. If I switch to tty ctrl+alt+F1, login and  run "sudo restart lightdm" I can switch back to the gui and will have the  full screen display. I have the same issue using either the netbook  display or external display.

---

### Post by mikewhatever on 2012-05-01
This is a known problem with gma500. Check out the [Poulsbo Wiki]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo#A12.04") for a permanent workaround.

PS: Might want to rethink the title.

---

