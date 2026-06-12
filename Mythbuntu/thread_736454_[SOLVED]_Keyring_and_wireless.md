---
title: "[SOLVED] Keyring and wireless"
date: 2008-03-26
forum: Mythbuntu
---

### Post by jakev383 on 2008-03-26
Okay, so I'm running a front end on wireless and it's connecting to my WPA network.  How do I get it to stop asking me for the keyring password? I've seen a few other threads concerning this, but none of them will work with auto-login enabled.  Does anyone have a solution?
Thanks in advance.

---

### Post by jakev383 on 2008-03-27
I went and installed Wicd and solved the problem ([http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)). Easy installation instructions - add the repo, install it (automatically removes network-manager and network-manager-gnome) then create a Startup for it. I also unchecked the nm-applet Startup while I was in there, made sure the only entries in /etc/network/interfaces were lo and rebooted.  When it came up I exited out of mythfrontend, and set up the wireless network profile (WPA encryption, DHCP). Rebooted to make sure it all worked and we're good!
Great little applet and easy to use.

---

