---
title: "Broadcom BCM4312 wireless card, ndiswrapper help"
date: 2009-12-27
forum: Networking &amp; Wireless
---

### Post by linc186 on 2009-12-27
I have a dell inspiron 1545 computer that came with windows 7. I dual booted it with ubuntu v.9.10. I discovered that my wireless card (which is a Broadcom BCM4312) apparently isn't compatible with ubuntu. So, i downloaded the needed driver and found the .inf file for my windows driver, but the read me included with the driver makes no sense to me - I can't understand the instruction because I'm still learning this code and downloaded ubuntu partially for that reason. So, if somebody can spell out those instructions in ENGLISH for me, the would be great! Thank you in advance.

-linc186

---

### Post by linc186 on 2009-12-27
anybody! Please! I'm really desperate now, and I need to use the internet.:confused:

---

### Post by bkratz on 2009-12-27
> **linc186 said:**
> anybody! Please! I'm really desperate now, and I need to use the internet.:confused:



Can you provide a link to the instructions you are having a problem with?


Actually a lot of people have success with the BCM4312 simply by (with a wired connection in)  

Look in System/Administration/Hardware Drivers and if it's there, enable the Broadcom STA driver. If it's an option, it's by far the simplest.

---

### Post by linc186 on 2009-12-27
> **bkratz said:**
> Can you provide a link to the instructions you are having a problem with?


Actually a lot of people have success with the BCM4312 simply by (with a wired connection in)  

Look in System/Administration/Hardware Drivers and if it's there, enable the Broadcom STA driver. If it's an option, it's by far the simplest.

[http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

Also, when i go in to hardware drivers, nothing at all appears. It tells me that there are propriety drivers.

---

### Post by coffeecat on 2009-12-27
> **linc186 said:**
> Also, when i go in to hardware drivers, nothing at all appears. It tells me that there are propriety drivers.

I presume you mean "**no** proprietary drivers". Without wireless you have to have a live wired connection for the Hardwire Drivers app to work. Are you connected with an ethernet cable? If so, open System > Administration > Update Manager and click on 'check' to download the package metadata, but **don't** do an update yet. Close update manager and open Hardware Drivers again. Any luck?

If that doesn't work, you can install the STA driver from the live Ubuntu CD. Have a look at post #1 here:

[http://ubuntuforums.org/showthread.php?t=1288865](http://ubuntuforums.org/showthread.php?t=1288865)

---

