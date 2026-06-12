---
title: "Sceptre Monitor and Nvida Drivers"
date: 2007-06-28
forum: Multimedia &amp; Video
---

### Post by TheJackofClubs on 2007-06-28
i got a really nice sceptre x20wg monitor that i really love and i really want nvidia drivers to work with it. i also have a geforce 4000 (not so fanceh nowadays). i installed reinstalled ubuntu and right away my monitor started in 1680x1050 which was surprising since all my friend with high res monitors had to add that into their xorg.conf. anyways, i set up my nvidia drivers the ubuntu way (system > administration > restricted drivers) and installed nvidia glx drivers. when it rebooted it and went into xserver the monitor says "out of range". i disabled the boot splash in menu.lst since it was saying out of range too when in it so i thought maybe (though unlikely but i did it anyways) that that was causing it to be a problem. i can do with out the splash screen anyways so i dont plan to reenable it right now even though it doesnt work with this monitor. but i can restart xserver by changing the driver from nvidia back to nv in xorg.conf. i wants me some beryl! so please help. :) im at a dead end in trying to figure this one out. thanks.

xorg.conf attached! weeeeeeeeeeeee!

---

### Post by TheJackofClubs on 2007-06-28
please help. ive tried everything i can think of. including reinstalling ubuntu. ive tried changing refresh rates though i have no clue what im doing when it comes to that so if anybody can help fill in the blanks thanks.

i get free copies of vista! dont tempt me! :)

---

### Post by TheJackofClubs on 2007-06-28
i just got it to work! :D i vnc'd into my comp with my mac and changed the refresh rate from 50 to 56 and it works. yay. thanks anyways.

---

