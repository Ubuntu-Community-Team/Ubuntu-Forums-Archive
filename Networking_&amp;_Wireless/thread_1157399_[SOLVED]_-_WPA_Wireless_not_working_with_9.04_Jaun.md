---
title: "[SOLVED] - WPA Wireless not working with 9.04 Jaunty Jackalope"
date: 2009-05-12
forum: Networking &amp; Wireless
---

### Post by linux.noob on 2009-05-12
This thread is solved.  I thought I would post this info to help someone else.
 Caution that I am a newbie, not an expert, but I got the feeling there are many more newbies like me out there.  I’ve gleaned a lot of good info on the forum pages and wanted to pay forward what I could.
 

 Problem:
 WPA wireless didn't work.  I have an old laptop (IBM T30) with a fairly new PCMCIA wireless card (D-Link DWA-652).  I installed Ubuntu to play with it and test stuff out.  I love it!
 

 Anyhow, I first installed 8.10 and struggled to get the wireless card to work properly.  I tried backports, ndiswrapper, etc.  I finally got the card to work with WPA2 at g speed.
 

 Then I upgraded (through the normal upgrade process) to 9.04 and the card didn’t work properly anymore.  It would only work on no security (wide open network) and WEP.  For obvious reasons I considered those unacceptable.  It would no longer work with WPA or WPA2, etc.  I tried several unsuccessful things:
 - I looked into WPA supplicant, this looked too intensive for a newbie and I suspected my problem was fairly simple to solve.
 - Tried installing backports, didn’t help me.
 - At bootup I tried going to the older kernel version (2.6.27-11), that seemed to work about 50% of the time.  Now that was really confusing, no consistency?
 - Tearing my hair out.
 

 Solution:
 Finally, I tried a live CD of 9.04 and booted off of that.  Wireless success!  In fact, it worked better than with 8.10.  By better I mean it connected in about 3 seconds versus about 20 with 8.10.
 

 So, I did a fresh install of 9.04 and it’s working perfectly now.  One note: I’ve noticed that every 20th or so boot of Ubuntu doesn’t fully load the Network Manager properly, so I just re-boot and it’s there then.  Ya know, every masterpiece has a few flaws.  This flaw was in 8.10 too.


 Fresh install versus upgrade:
 a) The upgrade keeps your existing add-on programs.  I actually wanted to smoke mine anyway as it was cluttered and messy, the clean install solved a few problems beyond my wireless.  Obviously back your files up regardless of what you’re doing.
 

 b) When installing fresh version, choose the Manual Partition option ([http://ubuntuforums.org/showthread.php?t=1152809&highlight=sda5](http://ubuntuforums.org/showthread.php?t=1152809&highlight=sda5)) or you can get 2 versions of 9.04 on your hard drive.  You don't want that.
 

  In Manual Partition, here is what I remember (I don’t have it in front of me) you need to:
 - Pick the disk partition; mine was “sd5” with Ubuntu
 - Click “Edit”
 - For file system option I picked the ext3, as the majority opinion seemed to say it was most stable, etc.
 - Check the format box
 - Pick the “/” option for mount point
 

 Good luck!

---

