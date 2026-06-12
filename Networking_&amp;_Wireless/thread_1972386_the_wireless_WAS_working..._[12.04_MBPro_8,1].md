---
title: "the wireless WAS working... [12.04 MBPro 8,1]"
date: 2012-05-03
forum: Networking &amp; Wireless
---

### Post by Samushighwind on 2012-05-03
I asked the apple users forum about this, but I might get more luck here...

So, I'm running Ubuntu 12.04 on a MacBook Pro 8,1.  I followed the instructions here word for word to get the wireless LAN working ([https://help.ubuntu.com/community/MacBookPro8-2/Oneiric#Wireless](https://help.ubuntu.com/community/MacBookPro8-2/Oneiric#Wireless)).  The only difference was that I installed linux-backports-modules-cw-3.3-precise-generic instead of linux-backports-modules-cw-3.2-oneiric-generic.

Worked really well.  Well, one of my friends was using my computer, I think he became frustrated with Linux, and I guess he just pressed the power button and switched to Windows (I triple boot with Mac and Windows).  I think that may have something to do with the problem-- the hard shutdown, I mean.

Well now whenever I boot up Ubuntu, my wireless doesn't work.  It used to list connections, but now it says "disconnected".  Even though "Enable wireless" is checked.

[IMG]http://oi49.tinypic.com/k03sqv.jpg[/IMG]

I have uninstalled all three relevant packages (mentioned in the how-to above) and reinstalled them, and then rebooted.  No fix.

help!!

---

### Post by TBABill on 2012-05-03
If the drivers are installed, have you tried to ```
sudo modprobe b43
```And if that works, then to make it persistent, just ```
gksudo gedit /etc/modules
``` and add "b43" without quotes to the list, save and restart to see if it held.

---

### Post by Samushighwind on 2012-05-03
typically it works on reboot.  and it randomly started working again.  but if I have this problem again, I might try that... though I'm not sure why it would make a difference.

thanks

---

