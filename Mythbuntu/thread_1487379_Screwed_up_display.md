---
title: "Screwed up display"
date: 2010-05-18
forum: Mythbuntu
---

### Post by gdselzer on 2010-05-18
I just finally installed 9.10 and now I've got crazy large fonts, menus, etc (screenshot attached.)  As you can see in the screenshot, the display resolution is set correctly (1920x1080) but everything looks like it's set to something much, much smaller.  This does not effect my usage of mythtv, but it makes changing anything on the system painful.

Any idea how do I fix this?

Thanks

---

### Post by gdselzer on 2010-05-25
bump

---

### Post by ian dobson on 2010-05-25
Hi,

305 dpi (dots per inch) looks far too high to me. Also your display is only 160mm x90mm and that can't be right. looks as if your display is handing out the wrong information, maybe try resetting the nvidia configurations back to default. Also have a look in /var/log/Xorg.log (Or something along those lines) for errors/warning.

Regards
Ian Dobson

---

### Post by Karim_ on 2010-05-25
Try deactivating the nvidia driver. I have problems, when I activate and deactivate the drivers the problems just disappear.

---

### Post by gdselzer on 2010-05-25
I have tried deactivating, rebooting, reactivating, and rebooting to no avail.

ian dobson, how do I reset the nvidia configurations back to defualt as you suggest?  I looked through the Xorg log (attached) and don't see any warnings or errors that pop out for me.

Thanks for the help.

---

### Post by Karim_ on 2010-05-26
Didn't see a difference when you deactivated the driver? So it didn't revert the screen to how ubuntu is installed (Normal, bulky and huge windows).

---

### Post by gdselzer on 2010-05-26
My bad Karim.  When I deactivated it I saw a difference (everything got very big and resolution was awful.)  When I reactivated it, it went back to looking like the picture I posted.  I even tried three different versions of the nvidia drivers to see if that made a difference (it didn't).

---

### Post by andree_b on 2010-05-27
Try setting a sane custom dpi (eg. 96) at [I]settings -> appearance -> fonts
[/I]

---

### Post by gdselzer on 2010-05-27
andree_b, you're a genius!  The default was set to 304.  I checked the "custom dpi" box and put 96 in.  Now it looks normal!  Not sure how (or where) the default was set to 304 but 96 appears to be the right number.

Thank you so very much for helping me get a usable interface.

---

