---
title: "Xfi and skype woes"
date: 2009-08-03
forum: Multimedia Software
---

### Post by fcuk112 on 2009-08-03
ok i recently had to reinstall ubuntu 9.04 and did some dicking around to get my XFi to work.  however, now my skype only gives me 3 options: default, hdmi and headset for some reason.

note sound is working through my XFi now, it's just skype that doesn't work.  i am also seeing some funny things now:

aplay -l returns
aplay: device_list:217: no soundcards found...

try to reinstall the XFi linux driver (sudo make install) returns:
Copy module files...
Update module dependency relationships...
FATAL: Error inserting ctxfi (/lib/modules/2.6.28-15-generic/kernel/drivers/ssound/ctxfi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
make: *** [install] Error 1

erm, how do i get out of this mess?

---

### Post by igorzwx on 2009-08-03
X-fi seems to be a problem indeed.

You may try to ask on OSS4 forum 
(they know everything about OSS and ALSA)

read this first:
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

**Does OSS Support My Hardware?**

 Check the list [here]("http://mercurial.opensound.com/?file/6bf18b4a87d6/devlists/Linux"). Some devices may not have full functionality (e.g. the X-fi module is limited to stereo output at the time of this writing, and jack sensing may not work on Azalia-compliant "High-Definition" devices, which are very common on motherboards and laptops today). If you're in doubt, consult the "Additional Support" sources found towards the end of this document. 
 
[B]
[/B]

---

