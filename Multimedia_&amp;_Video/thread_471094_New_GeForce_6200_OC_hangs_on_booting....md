---
title: "New GeForce 6200 OC hangs on booting..."
date: 2007-06-11
forum: Multimedia &amp; Video
---

### Post by Keiser on 2007-06-11
Ok.  

I just bought a new nVidia GeForce 6200 OC.

Plugged it up and tried booting up my existing Ubuntu install.  Expected it to bomb out starting X.  Planned on a dpkg reconfigure xserver-xorg.  No love.  Never even got that far.

Tried to boot into the rescue mode, still no love.

Removed new card and booted off the onboard video, copied off /home to different machine and reinstalled from scratch.

Normal CD hangs on hardware detection (I believe).
Alternate CD runs through entire install.  On reboot, machine hangs again on hardware detection, I believe.

Machine is an older Dell Optiplex GX260 tower, if that helps.

Any ideas on getting this installed?

Thanks!

---

### Post by francisco_athens on 2007-06-11
do you get a desktop using the live CD?  If this card is overclocked (assumed from the OC moniker) the issue may reside there.. also turn off the pc, remove and reinsert the card..

I had an issue on a p4p800 where I had to add "acpi=off nolapic" to the kernel options or I could not even boot! 
info here:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
What motherboard are you using?

---

