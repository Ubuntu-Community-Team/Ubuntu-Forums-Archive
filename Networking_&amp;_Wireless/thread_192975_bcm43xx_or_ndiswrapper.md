---
title: "bcm43xx or ndiswrapper?"
date: 2006-06-09
forum: Networking &amp; Wireless
---

### Post by glitch13 on 2006-06-09
I recently upgraded my Breezy laptop to Dapper and my Broadcom wifi card stopped working.  I was previously using ndiswrapper and it worked fine so I figured the upgrade hosed ndiswrapper.  After a lot of legwork I couldn't get it to work (it was complaining about a missing .fw file, something I've never seen with ndiswrapper).  I figured a clean Dapper install was in order to maybe eliminate any problems.  

Well after the install, lo and behold, my card was being recognized without ndiswrapper, but still had the same .fw file issue.  I slowly realized, as I'm sure you all did 10 seconds into reading this, that that Dapper now has the bcm43xx kernel module, which was apparenly "usurping" control from ndiswrapper after the upgrade, and that requires you to extract firmware from your win32 driver.  

I extracted the firmware from the driver that I *was* using with ndiswrapper and the error went away, but the thing still isn't working.   So out of curiousity I reinstalled ndiswrapper, rmmoded the bcm43xx, loaded ndiswrapper and bam, it works again.

So I guess I actually have two questions: 

-Can anyone give me any advice as to why my card isn't working with the bcm43xx/firmware setup?

-If I should just continue using ndiswrapper, how do I get Ubuntu to stop loading bcm43xx at boot and use ndiswrapper automatically?

---

### Post by ns2048 on 2006-06-10
>> Can anyone give me any advice as to why my card isn't working with the bcm43xx/firmware setup?
I seems only certain versions of this chipset are supported by the bcm43xx module.

>> If I should just continue using ndiswrapper, how do I get Ubuntu to stop loading bcm43xx at boot and use ndiswrapper automatically?

To prevent the bcm43xx module from being auto-loaded, add the following line to '/etc/modprobe.d/blacklist', then reboot

blacklist bcm43xx

Hope this helps.
--ns2048

---

### Post by glitch13 on 2006-06-14
If I blacklist the bcm43xx, how do I get the ndiswrapper module to autoload (sorry, I'm coming from a Gentoo background where things are a bit different).


And no one has any ideas on why the bcm43xx doesn't work in the first place?

---

### Post by HokeyFry on 2007-12-09
to make ndiswrapper load at startup add 

ndiswrapper

to the file /etc/modules

---

### Post by Ayuthia on 2007-12-09
If I recall, when you install the bcm43xx firmware, the driver does not come on automatically.  Once you load the module (via modprobe), you then need to turn on your wireless (by using sudo ifconfig <eth1/wlan0> up).  After that, you should be able to connect.  Like ndiswrapper, you have to add bcm43xx to /etc/modules so that it will automatically start on reboot.

---

