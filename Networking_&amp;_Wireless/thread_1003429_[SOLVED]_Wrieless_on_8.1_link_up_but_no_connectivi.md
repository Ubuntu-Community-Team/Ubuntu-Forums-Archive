---
title: "[SOLVED] Wrieless on 8.1 link up but no connectivity"
date: 2008-12-06
forum: Networking &amp; Wireless
---

### Post by Clivemunday on 2008-12-06
I have an ACER 4930G laptop and have just installed Ubuntu 8.1, updgrading from 8.04. The new version found my wireless adaptor which 8.04 did not. I can set it up, it automatically connects to my Buffalo router, it aquires an IP address and says it is up at 99% plus strength. But I cannot get any connectivity over the link I cannot even get a ping response from the router. Can anyone suggest how to get this working? 
My ethernet connection works but not really well it drops connections all the time and I cannot reconfigure the ethernet it tells me it is read only? Not sure if the problems are related.
Any pointers much appreciated.

Best regards,
Clive

---

### Post by Clivemunday on 2008-12-06
OK I have to set eth0 to down and then the wireless works just great. I have to do this after every restart is there a permanent cure for this problem?

Thanks,
Clive

---

### Post by Clivemunday on 2008-12-26
Just following up on this thread. I have now installed wicd and all the set up is automatic I no longer need to down eth0 to get wireless to work.
I downloaded the deb package from here:

[http://sourceforge.net/project/showfiles.php?group_id=194573&package_id=229460&release_id=649033](http://sourceforge.net/project/showfiles.php?group_id=194573&package_id=229460&release_id=649033)

I could not install it until I removed network-manager after this I ran the installer and restarted (not requested but I did it anyway.) On restart I looked in "Applcations Internet" and ran Wicd Manager. I entered the correct settings for my wireless router (connection type and passphrase / key) and clicked connect automatically. now each time I start my wireless connects and works every time.

Hope this helps someone.

Best regards,
Clive

---

