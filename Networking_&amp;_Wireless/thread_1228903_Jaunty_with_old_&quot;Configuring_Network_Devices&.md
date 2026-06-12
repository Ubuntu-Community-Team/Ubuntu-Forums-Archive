---
title: "Jaunty with old &quot;Configuring Network Devices&quot; problem."
date: 2009-08-01
forum: Networking &amp; Wireless
---

### Post by trevelyn on 2009-08-01
I thought this problem was fixed!?

Anyways, I DO NOT have NetworkManager, I have followed ALL of the old threads (that i could find) and commented out the eth0 lines in the /etc/network/interfaces files.  I have tried grepping files in /etc/rc*.d/* for "dhclient" and found nothing (so far).  I even set the cards to "manual" in the /etc/network/interfaces file!

the strangest thing about this.. I uncommented the "timeout 60" line in the dhclient.conf file, and it still hangs.. i even set the "60" to "5" and it still hangs, but here is the weird part.. it hangs FOREVER.  I reboot and dont boot into the live disk, and i get a inet connection with Windows instantly.. confusing.. :confused:

All the BUG's i went through on launchpad, and post i found about this issue in 8.10 and such, mentioned actually getting into the OS after waiting the 60 seconds, mine doesn't.. 

I am remastering my OS right now and have installed "WICd" as NetworkManager is 80MB's that i don't want to add to my ISO right now.

Anyone seen this in Jaunty? Anyone know what i should do?  I installed on my developoment box with a network connection and inet, so i am sure that dhclient and dhcp stuff is up to date (i hope).   

Thanks in advance!

---

### Post by trevelyn on 2009-08-01
I remembered about /etc/init.d/* and i looked at anything network related in /etc/init.d/ and found:

"networking"

which contains the string "Configuring Network Interfaces"

i copied it to my ~ dir and removed it from init.d dir.  I am now remastering the ISO again... I hope that this time it is in fact bootable.

EDIT:
ahh yes, i looked at its code and saw that it only calls ifup, which i thought used the config file 
/etc/network/interfaces - yet the devices are set to "manual" according to the syntax from the man pages.
and I also saw that if i did not have a usplash, which in fact as of now i dont, the timeout for the usplash is 2 minutes!

---

### Post by trevelyn on 2009-08-01
Fixed.  All i had to do is remove /etc/init.d/networking and remaster the ISO.  Maybe it has something to do with casper, maybe the live system re-writes that file..  when i searched /etc/network/interfaces contents it was completely different than what i had put in there.  thats most likely what was conflicting.

EDIT:
ahh, yes, i failed to mention that the interfaces where configured automatically.  now if i had say a wireless card that couldn't associate with an AP, would it fail once again?? I will try it:

---

