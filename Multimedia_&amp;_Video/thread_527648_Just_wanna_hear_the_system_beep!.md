---
title: "Just wanna hear the system beep!"
date: 2007-08-16
forum: Multimedia &amp; Video
---

### Post by EvilMarshmallow on 2007-08-16
I have been mucking around with my sound after installing Wolfenstein: Enemy Territory.  I now have sound working in rhythmbox, et, and I can click on a wav file and it will play.

However... (there's always a however!)  I have no system sounds.

My system is silent even though I've set all the system files to be attached to my nifty wav collection.  I don't get an error message when I use the sound test button on the sound control panel.  They just don't play.

All my other sound works.  Every app I've thrown at it, it's understood and worked wonderfully, thanks to the "Comprehensive Sound Guide" I found here on the forums.  But my system sounds are still quiet!  Can anyone help?

---

### Post by kyphi on 2007-08-16
Are system sounds enabled?

System -> Preferences -> Sound

Do you have a sound card or are you using the onboard sound chip?

---

### Post by EvilMarshmallow on 2007-08-17
System sounds were enabled.  I solved the problem and this is some weird stuff:

After I got all my other sound working (when I wrote the original post), system sounds were disabled.  I saw on another thread that some people had to enable the system sound mixing after performing some of the steps I followed.  So in desperation, I *DISABLED* the system sound mixing and OK'd it.  Then I went back in and re-enabled it... and it worked!

I now have all the sound working on my pc.  It's got an onboard audio card but I disabled that in the BIOS and I'm using a SB Audigy LS.

Can anyone help me understand why this worked?  Rebooting didn't work, but cycling that little switch did... and that doesn't make sense to me.  I'd have thought that a reboot would have done the same logical thing.  Is this a bug in Feisty, or what?

---

