---
title: "Unable to detect AP post-upgrade"
date: 2006-06-18
forum: Networking &amp; Wireless
---

### Post by Etoile on 2006-06-18
I have a Dell Inspiron 1150 laptop with built-in Broadcom wifi.

I upgraded from Breezy to Dapper and everything went fine - except now my wireless doesn't work.  Ndiswrapper is installed properly, I have Kwifimanager and it runs fine...it just doesn't seem to detect any AP.  When I boot into XP there are no problems, so I'm certain it's not my AP.

My lsmod showed extra drivers on usbcore (not sure why it's there, but that's where ndiswrapper was) so I did **sudo modprobe -r** for the two extra drivers.  I also did **sudo modprobe -r ndiswrapper** to clear that one off, and then **sudo modprobe ndiswrapper** to put it back.

Still nothing.  As far as I can tell, everything is fine - and Kwifimanager indicates that radio is on - and it's just not seeing my AP.  I have the correct SSID entered, too.  **sudo iwconfig eth1 up** doesn't help, though I did fail to copy the error message and will have to boot back into Ubuntu to get it.

I'm utterly baffled.  Any help?  Everything else is running great, so I'd hate to have to do a clean install just for this.

---

### Post by Etoile on 2006-06-19
I was a bit surprised to not get *any* responses on this.  Perhaps a bump will call the thread to the attention of someone who might be able to help?

Tonight I plan to try disabling ndiswrapper and seeing if the Dapper-native version will make it work instead, rather than disabling that and trying to force ndiswrapper to work.

---

### Post by trubblemaker on 2006-06-19
in dapper their is a native driver for broadcom and it conflicts with ndiswrapper, try on of the howto's below for the native driver or blacklist the native driver, steps to do that are listed in the howto below.

---

### Post by Etoile on 2006-06-19
I ended up renaming bcm43xx.ko (located in /lib/modules/[kernel version]/kernel/drivers/net/wireless/bcm43xx/ ) to bcm43xx.bak - after a reboot, it worked immediately.  Thanks!

---

