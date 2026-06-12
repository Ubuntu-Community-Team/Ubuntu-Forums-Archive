---
title: "Biostar TF8200 A2+ Has No Sound"
date: 2009-03-23
forum: Mythbuntu
---

### Post by techxpc on 2009-03-23
I have a Biostar TF8200 A2+ and I am getting no sound at all. I have verified that all cables are plugged in correctly and the sound configuration is set as default. I am using the newest version of Mythbuntu. Any help is appreciated. Thanks!

---

### Post by techxpc on 2009-03-24
This has the Geforce 8200. Is there anyone that knows how to get the sound to work. Just the on board sound would be fine. I was trying to get the sound to work over hdmi, but at this point I just need sound.

---

### Post by novellahub on 2009-03-24
I am working with techxpc on this issue.   The onboard sound is Realtek ALC888.  

[http://www.biostar.com.tw/app/en-us/t-series/content.php?S_ID=353](http://www.biostar.com.tw/app/en-us/t-series/content.php?S_ID=353)

If anyone has any ideas, please let us know.  We are contemplating upgrading ALSA from 1.0.17 to 1.0.19.  The install is Mythbuntu 8.10 x64.

---

### Post by novellahub on 2009-03-25
This is issue is now solved.  Techxpc got the sound to work by upgrading the Nvidia drivers to 180.29 and Alsa to 1.0.19 using a upgrade script found on these forums.  Then not using the on-board sound and going with sound over HDMI.

---

