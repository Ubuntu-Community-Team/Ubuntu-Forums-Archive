---
title: "Sony Bravia HDMI / HTPC input issues"
date: 2010-08-30
forum: Multimedia Software
---

### Post by ruger01 on 2010-08-30
Hi,
 
Wanted to know if anyone has a solution to the issue i have, when swapping HDMI inputs on my KDL46Z5500 Sony Bravia Tv i get a blank black screen when trying to display my HTPC. For example i can have the Tv on HDMI input 1 and boot the HTPC and all works perfectly well, but as soon as i change inputs to say the PS3 on HDMI 2 when i go to go back to the HTPC i get a blank black screen and no matter what i do i cannot get the picture to display, only solution is to reboot the sytem then it all works again. This is an issue as i am streaming movies through the PS3 from the HTPC and swapping back between devices is very handy.
 
The HTPC is a brand new sytem i built with the following board Gigabyte GA-880GM-USB3 and i use the onboard graphics ATI Radeon HD 4250 connected from HDMI port on the board to the Tv.
 
Does anyone know if this is an ATI driver issue? (i have the proprietory driver installed when i installed ubuntu 10.04) Is there any update, app or driver etc i can install to force the tv to detect the signal coming from the HTPC?
 
Would connecting via DVI make any difference, or say buying a Nvidia dedicated graphics card fix this issue? - Although if i spend one more sent my wife will kill me!:D
 
Any advise or a solution would be greatly appreciated,
 
Cheers Ruger01.

---

### Post by ruger01 on 2010-09-03
Now SOLVED - In my motherboard bios i had to go into the setting " Onboard VGA output connect" and select D-SUB/HDMI not as per the default setting of "AUTO" also with the Sony Bravia TV make sure the PC is connected to HDMI Input 1. Can swap inputs no issues anymore.

Very happy after tearing out hair for a week!

Cheers.

Ruger01.

---

### Post by ruger01 on 2010-09-06
But alas this is not working anymore! doh... can swap from input tuner i.e. watching normal tv to the htpc no worries now.
 
But when i swap input 2 (ps3) back to input 1 (htpc) I get the black screen still, have been reading up on this and apparently it is to do with EDID data being sent from the tv does anyone have a solution to fix this?
 
Is it possible to edit Xorg to set the tv up as the only display or something so when i swap back to HDMI 1 it just works on the resolution 1080p?
 
Please help really stumped on this one,

Cheers,

---

### Post by ruger01 on 2010-09-09
Well replying to myself here yet again but hope this helps someone else - I found a work around for this after reading millions of post from all over the net.

By using the keys on my keyboard "Ctrl + Alt + Backspace" you can restart the "X" server 

Go to your desktop in Ubuntu 10.04 System Tab - Preferences - Keyboard - Layouts Tab - Options Tab. Open the field that says "Key sequence to kill the X Server, and tick this to enable it.

When changing input to HDMI 2 back to HDMI 1 i press these and i get the screen back. Remember to log back in each time you get the desktop back otherwise the next time you go back and forward this key sequence won't work,

Hope this helps someone else,

Cheers Ruger01.

---

