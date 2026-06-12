---
title: "IPW2200 and WPA issues!"
date: 2005-12-09
forum: Networking &amp; Wireless
---

### Post by routerstu on 2005-12-09
As many people know there are some serious issues with the ipw2200 driver and wpa.  Has anyone gotten this to work under breezy?  i have tried the fix posted under hoary, installing the correct gcc but i used the latest driver/ieee and firmware.  now eth1 is gone stating something about an invalid character.  if someone know how to use wpa on ipw2200 please please please post a howto or give me a lead here and i will.  thanks

---

### Post by ape on 2005-12-09
I got ipw2200 and wpa working on my Hoary box and it continued to work after upgrading to Breezy.

Can you post the error messages you are getting?  Is the ipw2200 module loading or is that where you're getting the invalid character error?

---

### Post by hod139 on 2005-12-09
there is a howto for Hoary [here]("http://ubuntuforums.org/showthread.php?t=26623&highlight=wpa").  The howto is very long and some of the packages have newer versions and some of the configuartion advice has changed for Breezy.  There are some updates for Breezy hidden in the post though if you are willing to read through it all.  Another howto updated for breezy can be found on the ubuntu wiki [here]("https://wiki.ubuntu.com/WPAHowto?highlight=%28wpa%29").

Hope this helps some.

---

### Post by routerstu on 2005-12-09
thanks people!!! i am going to look into the wiki option.  this was a fresh install of breezy, so i could reinstall hoary then upgrade but seems iffy.  i will post dmesg soon.  also, when i followed the howto i did sway away in using the latest packages, which may have cause my issues.

thanks!

---

### Post by routerstu on 2005-12-09
dmesg says:


disagrees about version of symbol ieee80211xxxxxxxxxx

unknown symbol ieee80211xxxxxxx


i tried using the latest of firmware, ipw2200 driver and ieee80211.  any ideas?

---

