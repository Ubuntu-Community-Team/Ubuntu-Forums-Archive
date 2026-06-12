---
title: "9400GT can't get 50Hz over DVI"
date: 2009-03-04
forum: Mythbuntu
---

### Post by dado483 on 2009-03-04
Hi all,
i'm having trouble using a Club3d Nvidia 9400GT Silent 512MB under Linux Ubuntu Intrepid with 180.29 drivers. My HTPC is working using Mythtv rev. 20020 and VDPAU works great, but not at all because i've only 60Hz running...... 

I'm using my card connected to a BenQ PE7700 projector and i need to use 720Px50Hz resolution.

When the system start, Xorg get correctly Edid information from the projector, but when i try to set 720P resolution at 50Hz, the output is correctly displayed but at 60Hz. Setting refresh at 60Hz is correctly displayed at 60Hz.

So i've 720Px50Hz and 720Px60Hz modes, both displaying the image at 60Hz.
I've also tested my 9400GT with an Epson TW600 projector and the result is the same.

Anyone can help me?

Thanks!

P.S.: i've tested my projector with another pc, running ubuntu intrepid, 180.29 nvidia drivers and an Nvidia 6600GT video card, and with this one all is work correctly. With 6600GT i can obtain 720Px50Hz correctly.

---

### Post by rodercot on 2009-03-04
You may want to check out this thread.

 [http://ubuntuforums.org/showthread.php?t=194531](http://ubuntuforums.org/showthread.php?t=194531)

 you could edit your xorg.conf file and in the screen section add this option

 Option         "ModeValidation" "AllowNon60HzModes"

 Here is another thread about creating custom modelines and using them as well. 

  [http://ubuntuforums.org/showthread.php?t=1003099&page=2](http://ubuntuforums.org/showthread.php?t=1003099&page=2)

 rgds,
 
 Dave

---

### Post by dado483 on 2009-03-04
SOLVED!

Someone on nvidia forum give to me the trick!

I've put
Option "FlatPanelProperties" "Scaling = Native"
in my xorg.conf and now i'm able to set 50Hz over DVI at 1280x720

Thanks!

---

