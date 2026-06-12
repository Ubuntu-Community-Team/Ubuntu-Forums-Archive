---
title: "Problems getting Huawei e1750 to work with 10.04"
date: 2010-11-01
forum: Networking &amp; Wireless
---

### Post by olivaw_daneel on 2010-11-01
I've recently signed up for T-Mobile mobile broadband in the UK. I received a huawei e1750 usb stick to enable me to connect to the internet.

According to this thread [http://ubuntuforums.org/showthread.php?t=1246293](http://ubuntuforums.org/showthread.php?t=1246293) I should be able to get the dongle to work on Ubuntu 10.04. I've followed all the instructions in that post to get it to work but it just doesn't.

Despite having usb modeswitch installed whenever I plug the dongle in Ubuntu thinks it's a virtual CD drive.

What's very strange is if I type 'lsusb' into the terminal Ubuntu seems to think that the usb is a huawei e620 modem even though on the back of the stick it says it's an e1750.

I've also looked at instructions for getting an e620 to work and tried the dongle with wvdial but nothing's happening.

Does anyone have any additional ideas as to how I could get this dongle to work?

Thanks in advance.

---

### Post by olivaw_daneel on 2010-11-02
Bump.

I'm very confused why ubuntu is detecting the modem as an e620. Could this be the reason it's not working?

---

### Post by marbertone on 2010-11-02
Install gnome-ppp and try to match the right initialization settings for your modem. The trick is that every time you want to connect you have to be sudo, hence you could create a link to gnome-ppp on your desktop like this: gksudo gnome-ppp

Hope this helps!
Cheers!

p.s.
remove the pin from the sim, it's definitely easier to configure the modem w/out the pin.

M.A.

---

