---
title: "Making Wireless work on Compaq Laptop (V3019us)"
date: 2009-03-08
forum: Networking &amp; Wireless
---

### Post by MichaelSelf on 2009-03-08
Good Evening!

I just put a new HD in my laptop and I would like to run Ubuntu 8.10 on it.  So far, the only issue I've run into is wireless.  Through a little research I've learned that the laptop has some derivation of a Broadcom card.  I stumbed onto this thread, but I'm still relatively new at this and it was a little over my head.

[http://ubuntuforums.org/showthread.php?t=234424](http://ubuntuforums.org/showthread.php?t=234424)

Thanks in advance for the help!

---

### Post by Ayuthia on 2009-03-08
> **MichaelSelf said:**
> Good Evening!

I just put a new HD in my laptop and I would like to run Ubuntu 8.10 on it.  So far, the only issue I've run into is wireless.  Through a little research I've learned that the laptop has some derivation of a Broadcom card.  I stumbed onto this thread, but I'm still relatively new at this and it was a little over my head.

[http://ubuntuforums.org/showthread.php?t=234424](http://ubuntuforums.org/showthread.php?t=234424)

Thanks in advance for the help!

I am not for sure which Broadcom chipset you have, but if you have a working internet connection in Ubuntu, you should be able to go into System->Administration->Hardware Drivers and activate the Broadcom option.  If you have more than one option (Broadcom b43 or Broadcom STA), you can pick either one.  The b43 version is the open source version and the STA version is the proprietary version.  The b43 module does need to download a firmware file to make it work, but the STA version just needs to be activated (no internet connection needed).

Hope that helps.

---

### Post by Woodsyx on 2009-03-08
A side note if that doesnt work you should try NDISWrapper. 

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by MichaelSelf on 2009-03-15
After updates I now have the Broadcom Propietary drivers and after enabling them I'm still not having success.

This could be because of my lack of experience with ubuntu.  Should the wireless networks pop up for me to select them, or do I need to add them in first?  

If I need to first add them in...what information do I need and what are the proper steps?

---

