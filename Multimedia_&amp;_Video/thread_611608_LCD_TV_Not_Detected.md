---
title: "LCD TV Not Detected"
date: 2007-11-13
forum: Multimedia &amp; Video
---

### Post by Bleyze on 2007-11-13
I have a PowerPC MacMini with a Radeon 9200 video card. I am using the "Option MacModel mini" line and when I plug a CRT into the Mac Ubuntu works perfectly.

The problem I have is when I plug my LCD TV into the Mac I believe it is not being detected correctly and Ubuntu never launches into the GUI. I had a similar probelm with Feisty with this LCD TV. The solution with Fiesty was to plug the LCD TV in. Boot the Mac and remote control it with VNC from another PC and poke it till it worked.With Gutsy when the LCD is connected the drums never sound and I can't log into the GUI.

I have tried booting the Mac with the CRT plugged in then unplugging and connecting the LCD. When I d that xresprobe, EDID-Probe and lspci still show stats for the CRT. XrandR does show stats for the LCD. I have also tried booting the Mac with the LCD plugged in and then connecting a CRT. The CRT's (2)  have never been able to display a picture after doing this.

With this LCD TV I have never seen the character line boot information that I see with the CRT. With Feisty the first thing it would show in the boot process is the GUI logon. A CRT would show all the other stuff first. This means that if it is displaying a crash screen I can't read it.

I have commented out the  FailsafeXServer=/etc/gdm/failsafeXServer
in /etc/gdm/gdm.conf and I have tried using "Option IgnoreEDID  True".

I have also tried using the ATI VESA driver, I believe there is a PowerPC issue with that one because it couldn't launch X till I went back to the original driver. 

Does anyone have any ways of booting a Gutsy PC so that it can be logged into the GUI in such a way that it doesn't care what the monitor detects as. If I can launch the GUI with the LCD connected I can remote control it and take it from there but rigtht now it appears to be ignoring everything I put in the Xorg.conf when the LCD TV is plugged in.

Thanks

---

