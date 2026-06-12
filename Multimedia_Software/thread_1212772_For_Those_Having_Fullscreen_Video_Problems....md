---
title: "For Those Having Fullscreen Video Problems..."
date: 2009-07-14
forum: Multimedia Software
---

### Post by cottfcfan on 2009-07-14
If like me you are having problems with Fullscreen Video Crashes, Choppy streaming, and Jerky Video etc..... Try This:

edit the xorg file run this:

Code:

gksudo gedit /etc/X11/xorg.conf

Then add the following lines to the end of the file:

Code:

Section "DRI"
	Mode 0666
EndSection

Section "Extensions"
	Option "Composite" "Enable"
EndSection

This is not my workaround, I got it from another thread, I have no idea why it works, but it resolved all my video problems, and even made my system a whole lot more responsive.
 It might not work for everyone but try it and see.

---

### Post by lovinglinux on 2009-07-14
Yep, I suggest that too. It works great. Check other tips in these threads:

[**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567) 

[Tips: Things that might improve Jaunty performance](http://ubuntuforums.org/showthread.php?t=1152095)

---

### Post by cottfcfan on 2009-07-15
I can`t believe it!!
The above script worked perfectly for a day or 2.
Now after a couple of reboots my computer has regressed.
Much slower & choppy fullscreen video again.
Ive checked the Xorg file and the workaround is still there.
Any ideas anyone?

---

### Post by cottfcfan on 2009-07-16
Plz Help...
This is my situation.
I`m using the HD2400 Radeon Graphics card.
When I 1st install FLGRX from "Hardware Drivers" my system works well. But after the 1st reboot, i lose system responsiveness.
 so I tried the above Fix. It worked fantastic, until I closed down my system.
 Then I uninstalled graphics driver and installed the latest ATI one from their website. Again system back to normal. It seems that a lot of fixes work until I reboot. Then performance drops again and live streaming becomes choppy.
 Can anyone more knowledgable than me (and that will be most of you) tell me why this is happening? and if I can do anything about it?

---

### Post by cottfcfan on 2009-07-16
Think I may have found the reason.
When streaming from BBC iplayer in Normal screen using flash player, both my CPUs are showing between 60-80% usage using, so I would think they will be maxed out in Fullscreen Mode, hence the choppy video.
 I think ive seen this problem somewhere on the forum but can`t find it.
 Would really appreciate someones help with this one..

---

### Post by smuggly on 2009-07-16
Im having the same problems with F/S Except when i use movie player! Check it out if everyones is working the same it must not be a xorg problem? I think anyway,Seems logical.However i move over to someone with more know how....................smuggly



I Found A Work around Try this --sudo apt-get install fusion-icon
Then go to apps/sys tools/Compiz fusion icon The right click on icon,select window mgr Metacity. ( It changes to metacity U can change back when your done )
 Hope this helps.

---

### Post by cottfcfan on 2009-07-16
Thanx for your reply Smuggly,

I tried your workaround, but it made no real difference to me.
Thanx anyway.

Anyone else have a suggestion?

---

