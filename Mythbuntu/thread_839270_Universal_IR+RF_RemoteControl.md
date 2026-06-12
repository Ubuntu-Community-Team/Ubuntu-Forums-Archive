---
title: "Universal IR+RF RemoteControl"
date: 2008-06-24
forum: Mythbuntu
---

### Post by maymann on 2008-06-24
Hi all, I have a Mythbuntu 8.10 setup with diskless frontends that I would like to place in the attic.
Is there a universal RemoteControl that can boot/control/shutdown both my MythTV frontends (via RF, Bluetooth, WIFI, ?) and control my TV, Receiver, Xbox360 via IR?

I know of [**Logitech Harmony 890/895/1000**]("http://www.logitech.com/index.cfm/remotes/universal_remotes/devices/374&cl=us,en"), but:
1. Is it supported in MythBuntu 8.10 ?
2. Can I boot/shutdown frontends ?
3. Can it handle more than one extender (frontend) ?

Weaker alternatives:
[**Logitech UltraX Media Remote**]("http://www.mythtv.org/wiki/index.php/Logitech_UltraX_Media_Remote")
[**MythControl**]("http://sourceforge.net/projects/mythcontrol")
[**Mythetomer**]("http://netti.nic.fi/~icewood/mythetomer/index.php")
[**diNovo Mini**]("http://www.logitech.com/index.cfm/keyboards/keyboard/devices/3848&cl=us,en?WT.ac=mb|4527||hp")

Does anyone have any experience with a similar setup ?

Thanks in advance !

---

### Post by dmfrey on 2008-08-03
I use a Logitech Harmony 890 remote with my mythbuntu setup.  It uses the Microsoft MCE Remote Control lirc format and the usb ir receiver.  When you setup the Harmony, you can search for the Microsoft MCE remote (which is just a re-branded Phillips remote control).  You can do almost everything you are asking except the boot up with this remote control.  To achieve this, you have a few options.  1. use another pc or internet tablet (like the nokia n800) to network boot the device, 2. Some cases come with IMON receivers that attach to your motherboard in between the power button lead and the power switch header on the board.  This allows for IR signals to trigger the power on.  I am sure there are other methods to do this, but they are just a few.

Also, I am running Mythetomer on my nokia n800 and it interacts flawlessly with the mythtv.  You can setup profiles for each mythtv you have so it can control all your extenders.

I hope this helps.

---

### Post by volkswagner on 2008-08-03
The Gyration MCE remote may server you.  The tough issue is the power up.  Are you trying to do this via a cold boot, or wake from standby.  I am not sure if the usb receiver will have power during a power off state.

The following has great info on getting the unit working.  It has IR for three units plus the RF for the pc.  The slick feature is the Gyration mouse function.



[http://ubuntuforums.org/showthread.php?t=479897&highlight=evrouter]("http://ubuntuforums.org/showthread.php?t=479897&highlight=evrouter")

---

