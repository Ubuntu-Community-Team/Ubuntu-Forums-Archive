---
title: "Really weird Wi-Fi problems!"
date: 2013-03-25
forum: Networking &amp; Wireless
---

### Post by MASTER260 on 2013-03-25
Okay, so I'm running Joli OS, & everything was working fine until 1 day my internet access stopped working.  Even with the wireless turned on, half the time it wouldn't find wireless networks & half the time it would, but it would show the connecting icon for a nanosecond until showing the disconnected icon again.  Now, here's the thing.  My router uses WEP security, but half the time when I'd try to connect, it'd only give WPA as an option.  When it would do this, Connection Settings would actually show 2 copies of the same router listed.  Also, in the Connection Settings Auto eth0 would blink & I couldn't select it, & when I'd have my cursor over the nm-applet, the words, "No network connection," would blink between that & something I couldn't read cuz it was going too fast.  Here's what's REALLY weird, though.  When I deleted my router from Connection Settings, everything would appear normal.  It even found an unsecured network for a tiny bit, & could connect!  But when I try to connect to my router again... all the problems resurface.  Also, one of the times I shut down my computer, it said something about keys...


...Which is why I'm wondering if it has something to do with my WEP security.  Any ideas?

Thanks,
M260.

EDIT: Oh, yeah, the router still works with other devices.

---

### Post by MASTER260 on 2013-03-25
bump.  Anyone gonna help?

---

### Post by wildmanne39 on 2013-03-25
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file.
Thanks

---

