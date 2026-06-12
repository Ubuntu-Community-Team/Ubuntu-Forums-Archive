---
title: "mythtv .20 - install lirc mce2 ontop of i2c?"
date: 2006-12-17
forum: Multimedia &amp; Video
---

### Post by tfmccull on 2006-12-17
myth .20 install on edgy. everything is working great, but i would like to use the usb receiver/mce remote that i have instead of the one i'm currently using (hauppague 150 remote). 

My last attempt at this ended with me reinstalling everything over again, and i'd prefer not to do that.

what is the correct procedure for doing this. Again, i have LIRC installed and running great with the i2c drivers.

I orginally followed superm1's howto at: [https://help.ubuntu.com/community/Install_Lirc_Edgy](https://help.ubuntu.com/community/Install_Lirc_Edgy)

Thanks.

---

### Post by superm1 on 2006-12-18
> **tfmccull said:**
> myth .20 install on edgy. everything is working great, but i would like to use the usb receiver/mce remote that i have instead of the one i'm currently using (hauppague 150 remote). 

My last attempt at this ended with me reinstalling everything over again, and i'd prefer not to do that.

what is the correct procedure for doing this. Again, i have LIRC installed and running great with the i2c drivers.

I orginally followed superm1's howto at: [https://help.ubuntu.com/community/Install_Lirc_Edgy](https://help.ubuntu.com/community/Install_Lirc_Edgy)

Thanks.
Hi,
basically you will have to run dpkg-reconfigure lirc-modules-source and choose the mceusb2 module instead.  Follow the steps to rebuild the modules at the end of the howto.  Add the mceusb2 remote information to /etc/lirc/lircd.conf.  Update your ~/.lircrc to match mceusb2 remote info if its different then your i2c remote.

---

